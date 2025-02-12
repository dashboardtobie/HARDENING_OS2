# Part III : Service Hardening

## 1. NGINX Tracing

🌞 **Tracer l'exécution du programme NGINX**

- lancer NGINX à la main, et utilisez `strace` ou `sysdig` pour voir tous les appels systèmes qu'il effectue
- visitez la page web d'accueil pendant que vous tracez l'exécution, pour voir les *syscalls*  nécessaires lors d'un fonctionnement normal
- dans le compte-rendu, listez tous les *syscalls*  passés par NGINX
```
[dash@localhost ~]$ sudo sysdig proc.name=nginx > trace_nginx.log
[dash@localhost ~]$ sudo cat trace_nginx.log | cut -d' ' -f7 | sort | uniq | tr '\n' ' ' 
access arch_prctl bind brk clone close connect dup2 epoll_create epoll_create1 epoll_ctl epoll_wait eventfd2 execve exit_group fcntl fstat futex getdents64 geteuid getpid getppid getrandom ioctl io_setup listen lseek mkdir mmap mprotect munmap newfstatat openat prctl read recvfrom recvmsg rseq rt_sigaction rt_sigprocmask rt_sigreturn rt_sigsuspend sendmsg sendto setgid setgroups setitimer set_robust_list setsockopt set_tid_address setuid socket socketpair statfs  sysinfo timerfd_create timerfd_settime uname unlink wait4

```

## 2. NGINX Hardening

🌞 **HARDEN**

- modifier le fichier `nginx.service` pour inclure un filtrage des *syscalls*
- principe du moindre privilège : vous n'autorisez que le strict nécessaire
- vous me remettez le fichier `nginx.service` modifié dans le compte-rendu naturellement !  
[nginx.service](nginx.service)
