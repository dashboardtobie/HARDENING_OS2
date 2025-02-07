# Part III : Service Hardening

## 1. NGINX Tracing

🌞 **Tracer l'exécution du programme NGINX**

- lancer NGINX à la main, et utilisez `strace` ou `sysdig` pour voir tous les appels systèmes qu'il effectue
- visitez la page web d'accueil pendant que vous tracez l'exécution, pour voir les *syscalls*  nécessaires lors d'un fonctionnement normal
- dans le compte-rendu, listez tous les *syscalls*  passés par NGINX
```
[dash@localhost ~]$ sudo sysdig proc.name=nginx
2772 21:14:45.896178359 0 nginx (6232.6232) < epoll_wait res=1
2773 21:14:45.896303319 0 nginx (6232.6232) > accept4 flags=0
2774 21:14:45.896426185 0 nginx (6232.6232) < accept4 fd=3(<4t>192.168.133.1:61161->192.168.133.129:80) tuple=192.168.133.1:61161->192.168.133.129:80 queuepct=0 queuelen=0 queuemax=511
2775 21:14:45.896463240 0 nginx (6232.6232) > epoll_ctl 
2776 21:14:45.896498873 0 nginx (6232.6232) < epoll_ctl 
2777 21:14:45.896513135 0 nginx (6232.6232) > epoll_wait maxevents=512
2778 21:14:45.896568110 0 nginx (6232.6232) > switch next=6239(NetworkManager) pgft_maj=0 pgft_min=300 vm_size=15532 vm_rss=5560 vm_swap=0
2780 21:14:45.898127747 0 nginx (6232.6232) < epoll_wait res=1
2781 21:14:45.898161221 0 nginx (6232.6232) > recvfrom fd=3(<4t>192.168.133.1:61161->192.168.133.129:80) size=1024
2782 21:14:45.898226897 0 nginx (6232.6232) < recvfrom res=585 data=GET / HTTP/1.1..Host: 192.168.133.129..Connection: keep-alive..Cache-Control: ma tuple=192.168.133.1:61161->192.168.133.129:80
2783 21:14:45.898584206 0 nginx (6232.6232) > newfstatat 
2784 21:14:45.898690541 0 nginx (6232.6232) < newfstatat res=0 dirfd=-100(AT_FDCWD) path=/usr/share/nginx/html/index.html flags=0
2785 21:14:45.899613258 0 nginx (6232.6232) > openat dirfd=-100(AT_FDCWD) name=/usr/share/nginx/html/index.html flags=65(O_NONBLOCK|O_RDONLY) mode=0
2786 21:14:45.899784641 0 nginx (6232.6232) < openat fd=12(<f>/usr/share/nginx/html/index.html) dirfd=-100(AT_FDCWD) name=/usr/share/nginx/html/index.html flags=65(O_NONBLOCK|O_RDONLY) mode=0 dev=FD00 ino=12783086
2787 21:14:45.899806685 0 nginx (6232.6232) > fstat fd=12(<f>/usr/share/nginx/html/index.html)
2788 21:14:45.899822141 0 nginx (6232.6232) < fstat res=0
2789 21:14:45.900198302 0 nginx (6232.6232) > writev fd=3(<4t>192.168.133.1:61161->192.168.133.129:80) size=181
2790 21:14:45.900895401 0 nginx (6232.6232) < writev res=181 data=HTTP/1.1 304 Not Modified..Server: nginx/1.20.1..Date: Thu, 06 Feb 2025 20:14:45
2791 21:14:45.900957029 0 nginx (6232.6232) > write fd=5(<f>/var/log/nginx/access.log) size=206
2792 21:14:45.901312970 0 nginx (6232.6232) < write res=206 data=192.168.133.1 - - [06/Feb/2025:21:14:45 +0100] "GET / HTTP/1.1" 304 0 "-" "Mozil
2793 21:14:45.901332062 0 nginx (6232.6232) > close fd=12(<f>/usr/share/nginx/html/index.html)
2794 21:14:45.901358828 0 nginx (6232.6232) < close res=0
2795 21:14:45.901635128 0 nginx (6232.6232) > setsockopt 
2796 21:14:45.902154951 0 nginx (6232.6232) > switch next=16 pgft_maj=0 pgft_min=300 vm_size=15532 vm_rss=5560 vm_swap=0
2799 21:14:45.902258735 0 nginx (6232.6232) < setsockopt res=0 fd=3(<4t>192.168.133.1:61161->192.168.133.129:80) level=2(SOL_TCP) optname=0(UNKNOWN) val=.... optlen=4
2800 21:14:45.902294933 0 nginx (6232.6232) > epoll_wait maxevents=512
2801 21:14:45.902323674 0 nginx (6232.6232) > switch next=6239(NetworkManager) pgft_maj=0 pgft_min=300 vm_size=15532 vm_rss=5560 vm_swap=0
```

## 2. NGINX Hardening

🌞 **HARDEN**

- modifier le fichier `nginx.service` pour inclure un filtrage des *syscalls*
- principe du moindre privilège : vous n'autorisez que le strict nécessaire
- vous me remettez le fichier `nginx.service` modifié dans le compte-rendu naturellement !
