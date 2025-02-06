# Part II : Observe

Si on veut tracer un processus avec `strace`, c'est comme ça :

```bash
# pour tracer l'exécution d'un echo par exemple
$ strace echo yo
```

🌞 **Utiliser `strace` pour tracer l'exécution de la commande `ls`**

- faites `ls` sur un dossier qui contient des trucs
```
[dash@localhost ~]$ strace ls
execve("/usr/bin/ls", ["ls"], 0x7ffc2e0c8b40 /* 31 vars */) = 0
brk(NULL)                               = 0x55bd64b4d000
arch_prctl(0x3001 /* ARCH_??? */, 0x7ffc924b52d0) = -1 EINVAL (Invalid argument)
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=13675, ...}) = 0
mmap(NULL, 13675, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fee04cdc000
close(3)                                = 0
openat(AT_FDCWD, "/lib64/libselinux.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0pp\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=175760, ...}) = 0
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fee04cda000
mmap(NULL, 181896, PROT_READ, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fee04cad000
mmap(0x7fee04cb3000, 110592, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6000) = 0x7fee04cb3000
mmap(0x7fee04cce000, 32768, PROT_READ, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x21000) = 0x7fee04cce000
mmap(0x7fee04cd6000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x28000) = 0x7fee04cd6000
mmap(0x7fee04cd8000, 5768, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fee04cd8000
close(3)                                = 0
openat(AT_FDCWD, "/lib64/libcap.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P'\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=36304, ...}) = 0
mmap(NULL, 36920, PROT_READ, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fee04ca3000
mmap(0x7fee04ca5000, 16384, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7fee04ca5000
mmap(0x7fee04ca9000, 8192, PROT_READ, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6000) = 0x7fee04ca9000
mmap(0x7fee04cab000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x7000) = 0x7fee04cab000
close(3)                                = 0
openat(AT_FDCWD, "/lib64/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0p\0\4\0\0\0\0\0"..., 832) = 832
pread64(3, "\6\0\0\0\4\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0"..., 784, 64) = 784
pread64(3, "\4\0\0\0 \0\0\0\5\0\0\0GNU\0\2\0\0\300\4\0\0\0\3\0\0\0\0\0\0\0"..., 48, 848) = 48
pread64(3, "\4\0\0\0\24\0\0\0\3\0\0\0GNU\0\353|1\205uO9\255\311\361\31#\314\366T\354"..., 68, 896) = 68
fstat(3, {st_mode=S_IFREG|0755, st_size=2387008, ...}) = 0
pread64(3, "\6\0\0\0\4\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0"..., 784, 64) = 784
mmap(NULL, 2133936, PROT_READ, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fee04a00000
mprotect(0x7fee04a28000, 1892352, PROT_NONE) = 0
mmap(0x7fee04a28000, 1527808, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x28000) = 0x7fee04a28000
mmap(0x7fee04b9d000, 360448, PROT_READ, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x19d000) = 0x7fee04b9d000
mmap(0x7fee04bf6000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1f5000) = 0x7fee04bf6000
mmap(0x7fee04bfc000, 53168, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fee04bfc000
close(3)                                = 0
openat(AT_FDCWD, "/lib64/libpcre2-8.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220$\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=636848, ...}) = 0
mmap(NULL, 635440, PROT_READ, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fee04964000
mmap(0x7fee04966000, 446464, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7fee04966000
mmap(0x7fee049d3000, 176128, PROT_READ, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6f000) = 0x7fee049d3000
mmap(0x7fee049fe000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x99000) = 0x7fee049fe000
close(3)                                = 0
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fee04ca1000
arch_prctl(ARCH_SET_FS, 0x7fee04ca1c40) = 0
set_tid_address(0x7fee04ca1f10)         = 12952
set_robust_list(0x7fee04ca1f20, 24)     = 0
rseq(0x7fee04ca25e0, 0x20, 0, 0x53053053) = 0
mprotect(0x7fee04bf6000, 16384, PROT_READ) = 0
mprotect(0x7fee049fe000, 4096, PROT_READ) = 0
mprotect(0x7fee04cab000, 4096, PROT_READ) = 0
mprotect(0x7fee04cd6000, 4096, PROT_READ) = 0
mprotect(0x55bd63ca9000, 8192, PROT_READ) = 0
mprotect(0x7fee04d14000, 8192, PROT_READ) = 0
prlimit64(0, RLIMIT_STACK, NULL, {rlim_cur=8192*1024, rlim_max=RLIM64_INFINITY}) = 0
munmap(0x7fee04cdc000, 13675)           = 0
prctl(PR_CAPBSET_READ, CAP_MAC_OVERRIDE) = 1
prctl(PR_CAPBSET_READ, 0x30 /* CAP_??? */) = -1 EINVAL (Invalid argument)
prctl(PR_CAPBSET_READ, CAP_CHECKPOINT_RESTORE) = 1
prctl(PR_CAPBSET_READ, 0x2c /* CAP_??? */) = -1 EINVAL (Invalid argument)
prctl(PR_CAPBSET_READ, 0x2a /* CAP_??? */) = -1 EINVAL (Invalid argument)
prctl(PR_CAPBSET_READ, 0x29 /* CAP_??? */) = -1 EINVAL (Invalid argument)
statfs("/sys/fs/selinux", {f_type=SELINUX_MAGIC, f_bsize=4096, f_blocks=0, f_bfree=0, f_bavail=0, f_files=0, f_ffree=0, f_fsid={val=[0, 0]}, f_namelen=255, f_frsize=4096, f_flags=ST_VALID|ST_NOSUID|ST_NOEXEC|ST_RELATIME}) = 0
statfs("/sys/fs/selinux", {f_type=SELINUX_MAGIC, f_bsize=4096, f_blocks=0, f_bfree=0, f_bavail=0, f_files=0, f_ffree=0, f_fsid={val=[0, 0]}, f_namelen=255, f_frsize=4096, f_flags=ST_VALID|ST_NOSUID|ST_NOEXEC|ST_RELATIME}) = 0
getrandom("\x65\xa5\x25\x4b\xb9\xb6\x5f\x58", 8, GRND_NONBLOCK) = 8
brk(NULL)                               = 0x55bd64b4d000
brk(0x55bd64b6e000)                     = 0x55bd64b6e000
access("/etc/selinux/config", F_OK)     = 0
openat(AT_FDCWD, "/usr/lib/locale/locale-archive", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale/locale.alias", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=2998, ...}) = 0
read(3, "# Locale name alias data base.\n#"..., 4096) = 2998
read(3, "", 4096)                       = 0
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_IDENTIFICATION", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_IDENTIFICATION", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=369, ...}) = 0
mmap(NULL, 369, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fee04d13000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib64/gconv/gconv-modules.cache", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=26988, ...}) = 0
mmap(NULL, 26988, PROT_READ, MAP_SHARED, 3, 0) = 0x7fee04c9a000
close(3)                                = 0
futex(0x7fee04bfba6c, FUTEX_WAKE_PRIVATE, 2147483647) = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_MEASUREMENT", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_MEASUREMENT", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=23, ...}) = 0
mmap(NULL, 23, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fee04cdf000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_TELEPHONE", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_TELEPHONE", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=59, ...}) = 0
mmap(NULL, 59, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fee04cde000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_ADDRESS", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_ADDRESS", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=167, ...}) = 0
mmap(NULL, 167, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fee04cdd000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_NAME", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_NAME", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=77, ...}) = 0
mmap(NULL, 77, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fee04cdc000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_PAPER", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_PAPER", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=34, ...}) = 0
mmap(NULL, 34, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fee04c99000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_MESSAGES", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_MESSAGES", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFDIR|0755, st_size=29, ...}) = 0
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=57, ...}) = 0
mmap(NULL, 57, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fee04c98000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_MONETARY", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_MONETARY", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=286, ...}) = 0
mmap(NULL, 286, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fee04c97000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_COLLATE", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_COLLATE", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=2586930, ...}) = 0
mmap(NULL, 2586930, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fee04600000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_TIME", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_TIME", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=3284, ...}) = 0
mmap(NULL, 3284, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fee04c96000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_NUMERIC", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_NUMERIC", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=54, ...}) = 0
mmap(NULL, 54, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fee04c95000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_CTYPE", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_CTYPE", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=346132, ...}) = 0
mmap(NULL, 346132, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fee04c40000
close(3)                                = 0
ioctl(1, TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(1, TIOCGWINSZ, {ws_row=33, ws_col=170, ws_xpixel=0, ws_ypixel=0}) = 0
openat(AT_FDCWD, ".", O_RDONLY|O_NONBLOCK|O_CLOEXEC|O_DIRECTORY) = 3
fstat(3, {st_mode=S_IFDIR|0700, st_size=62, ...}) = 0
getdents64(3, 0x55bd64b57580 /* 5 entries */, 32768) = 152
getdents64(3, 0x55bd64b57580 /* 0 entries */, 32768) = 0
close(3)                                = 0
close(1)                                = 0
close(2)                                = 0
exit_group(0)                           = ?
+++ exited with 0 +++
[dash@localhost ~]$ ls
[dash@localhost ~]$ strace ls /tmp
execve("/usr/bin/ls", ["ls", "/tmp"], 0x7ffcb267a148 /* 31 vars */) = 0
brk(NULL)                               = 0x5602bcc1a000
arch_prctl(0x3001 /* ARCH_??? */, 0x7ffeaac95da0) = -1 EINVAL (Invalid argument)
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=13675, ...}) = 0
mmap(NULL, 13675, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f6f2d634000
close(3)                                = 0
openat(AT_FDCWD, "/lib64/libselinux.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0pp\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=175760, ...}) = 0
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f6f2d632000
mmap(NULL, 181896, PROT_READ, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f6f2d605000
mmap(0x7f6f2d60b000, 110592, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6000) = 0x7f6f2d60b000
mmap(0x7f6f2d626000, 32768, PROT_READ, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x21000) = 0x7f6f2d626000
mmap(0x7f6f2d62e000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x28000) = 0x7f6f2d62e000
mmap(0x7f6f2d630000, 5768, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f6f2d630000
close(3)                                = 0
openat(AT_FDCWD, "/lib64/libcap.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P'\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=36304, ...}) = 0
mmap(NULL, 36920, PROT_READ, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f6f2d5fb000
mmap(0x7f6f2d5fd000, 16384, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7f6f2d5fd000
mmap(0x7f6f2d601000, 8192, PROT_READ, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6000) = 0x7f6f2d601000
mmap(0x7f6f2d603000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x7000) = 0x7f6f2d603000
close(3)                                = 0
openat(AT_FDCWD, "/lib64/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0p\0\4\0\0\0\0\0"..., 832) = 832
pread64(3, "\6\0\0\0\4\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0"..., 784, 64) = 784
pread64(3, "\4\0\0\0 \0\0\0\5\0\0\0GNU\0\2\0\0\300\4\0\0\0\3\0\0\0\0\0\0\0"..., 48, 848) = 48
pread64(3, "\4\0\0\0\24\0\0\0\3\0\0\0GNU\0\353|1\205uO9\255\311\361\31#\314\366T\354"..., 68, 896) = 68
fstat(3, {st_mode=S_IFREG|0755, st_size=2387008, ...}) = 0
pread64(3, "\6\0\0\0\4\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0"..., 784, 64) = 784
mmap(NULL, 2133936, PROT_READ, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f6f2d200000
mprotect(0x7f6f2d228000, 1892352, PROT_NONE) = 0
mmap(0x7f6f2d228000, 1527808, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x28000) = 0x7f6f2d228000
mmap(0x7f6f2d39d000, 360448, PROT_READ, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x19d000) = 0x7f6f2d39d000
mmap(0x7f6f2d3f6000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1f5000) = 0x7f6f2d3f6000
mmap(0x7f6f2d3fc000, 53168, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f6f2d3fc000
close(3)                                = 0
openat(AT_FDCWD, "/lib64/libpcre2-8.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220$\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=636848, ...}) = 0
mmap(NULL, 635440, PROT_READ, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f6f2d55f000
mmap(0x7f6f2d561000, 446464, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7f6f2d561000
mmap(0x7f6f2d5ce000, 176128, PROT_READ, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6f000) = 0x7f6f2d5ce000
mmap(0x7f6f2d5f9000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x99000) = 0x7f6f2d5f9000
close(3)                                = 0
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f6f2d55d000
arch_prctl(ARCH_SET_FS, 0x7f6f2d55dc40) = 0
set_tid_address(0x7f6f2d55df10)         = 12957
set_robust_list(0x7f6f2d55df20, 24)     = 0
rseq(0x7f6f2d55e5e0, 0x20, 0, 0x53053053) = 0
mprotect(0x7f6f2d3f6000, 16384, PROT_READ) = 0
mprotect(0x7f6f2d5f9000, 4096, PROT_READ) = 0
mprotect(0x7f6f2d603000, 4096, PROT_READ) = 0
mprotect(0x7f6f2d62e000, 4096, PROT_READ) = 0
mprotect(0x5602bc9aa000, 8192, PROT_READ) = 0
mprotect(0x7f6f2d66c000, 8192, PROT_READ) = 0
prlimit64(0, RLIMIT_STACK, NULL, {rlim_cur=8192*1024, rlim_max=RLIM64_INFINITY}) = 0
munmap(0x7f6f2d634000, 13675)           = 0
prctl(PR_CAPBSET_READ, CAP_MAC_OVERRIDE) = 1
prctl(PR_CAPBSET_READ, 0x30 /* CAP_??? */) = -1 EINVAL (Invalid argument)
prctl(PR_CAPBSET_READ, CAP_CHECKPOINT_RESTORE) = 1
prctl(PR_CAPBSET_READ, 0x2c /* CAP_??? */) = -1 EINVAL (Invalid argument)
prctl(PR_CAPBSET_READ, 0x2a /* CAP_??? */) = -1 EINVAL (Invalid argument)
prctl(PR_CAPBSET_READ, 0x29 /* CAP_??? */) = -1 EINVAL (Invalid argument)
statfs("/sys/fs/selinux", {f_type=SELINUX_MAGIC, f_bsize=4096, f_blocks=0, f_bfree=0, f_bavail=0, f_files=0, f_ffree=0, f_fsid={val=[0, 0]}, f_namelen=255, f_frsize=4096, f_flags=ST_VALID|ST_NOSUID|ST_NOEXEC|ST_RELATIME}) = 0
statfs("/sys/fs/selinux", {f_type=SELINUX_MAGIC, f_bsize=4096, f_blocks=0, f_bfree=0, f_bavail=0, f_files=0, f_ffree=0, f_fsid={val=[0, 0]}, f_namelen=255, f_frsize=4096, f_flags=ST_VALID|ST_NOSUID|ST_NOEXEC|ST_RELATIME}) = 0
getrandom("\x3a\x12\xbf\xfe\x75\x3e\x6b\xf9", 8, GRND_NONBLOCK) = 8
brk(NULL)                               = 0x5602bcc1a000
brk(0x5602bcc3b000)                     = 0x5602bcc3b000
access("/etc/selinux/config", F_OK)     = 0
openat(AT_FDCWD, "/usr/lib/locale/locale-archive", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale/locale.alias", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=2998, ...}) = 0
read(3, "# Locale name alias data base.\n#"..., 4096) = 2998
read(3, "", 4096)                       = 0
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_IDENTIFICATION", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_IDENTIFICATION", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=369, ...}) = 0
mmap(NULL, 369, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f6f2d66b000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib64/gconv/gconv-modules.cache", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=26988, ...}) = 0
mmap(NULL, 26988, PROT_READ, MAP_SHARED, 3, 0) = 0x7f6f2d556000
close(3)                                = 0
futex(0x7f6f2d3fba6c, FUTEX_WAKE_PRIVATE, 2147483647) = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_MEASUREMENT", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_MEASUREMENT", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=23, ...}) = 0
mmap(NULL, 23, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f6f2d637000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_TELEPHONE", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_TELEPHONE", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=59, ...}) = 0
mmap(NULL, 59, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f6f2d636000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_ADDRESS", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_ADDRESS", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=167, ...}) = 0
mmap(NULL, 167, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f6f2d635000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_NAME", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_NAME", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=77, ...}) = 0
mmap(NULL, 77, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f6f2d634000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_PAPER", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_PAPER", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=34, ...}) = 0
mmap(NULL, 34, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f6f2d555000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_MESSAGES", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_MESSAGES", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFDIR|0755, st_size=29, ...}) = 0
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=57, ...}) = 0
mmap(NULL, 57, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f6f2d554000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_MONETARY", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_MONETARY", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=286, ...}) = 0
mmap(NULL, 286, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f6f2d553000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_COLLATE", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_COLLATE", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=2586930, ...}) = 0
mmap(NULL, 2586930, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f6f2ce00000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_TIME", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_TIME", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=3284, ...}) = 0
mmap(NULL, 3284, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f6f2d552000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_NUMERIC", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_NUMERIC", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=54, ...}) = 0
mmap(NULL, 54, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f6f2d551000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_CTYPE", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_CTYPE", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=346132, ...}) = 0
mmap(NULL, 346132, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f6f2d4fc000
close(3)                                = 0
ioctl(1, TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(1, TIOCGWINSZ, {ws_row=33, ws_col=170, ws_xpixel=0, ws_ypixel=0}) = 0
statx(AT_FDCWD, "/tmp", AT_STATX_SYNC_AS_STAT|AT_NO_AUTOMOUNT, STATX_MODE, {stx_mask=STATX_BASIC_STATS|STATX_MNT_ID, stx_attributes=0, stx_mode=S_IFDIR|S_ISVTX|0777, stx_size=4096, ...}) = 0
openat(AT_FDCWD, "/tmp", O_RDONLY|O_NONBLOCK|O_CLOEXEC|O_DIRECTORY) = 3
fstat(3, {st_mode=S_IFDIR|S_ISVTX|0777, st_size=4096, ...}) = 0
getdents64(3, 0x5602bcc245c0 /* 9 entries */, 32768) = 472
getdents64(3, 0x5602bcc245c0 /* 0 entries */, 32768) = 0
close(3)                                = 0
fstat(1, {st_mode=S_IFCHR|0620, st_rdev=makedev(0x88, 0), ...}) = 0
write(1, "systemd-private-de678db24d5b435b"..., 156systemd-private-de678db24d5b435ba8f4ea798fae66c2-chronyd.service-AiNYiX      systemd-private-de678db24d5b435ba8f4ea798fae66c2-systemd-logind.service-C1sU5A
) = 156
write(1, "systemd-private-de678db24d5b435b"..., 76systemd-private-de678db24d5b435ba8f4ea798fae66c2-dbus-broker.service-JKaOfK
) = 76
close(1)                                = 0
close(2)                                = 0
exit_group(0)                           = ?
+++ exited with 0 +++
```
- mettez en évidence le *syscall* pour écrire dans le terminal le résultat du `ls`
```
[dash@localhost ~]$ strace ls /tmp 2>&1 | grep -E 'write|writev'
write(1, "systemd-private-de678db24d5b435b"..., 227systemd-private-de678db24d5b435ba8f4ea798fae66c2-chronyd.service-AiNYiX
```

🌞 **Utiliser `strace` pour tracer l'exécution de la commande `cat`**

- faites `cat` sur un fichier qui contient des trucs
```
```
[dash@localhost ~]$ strace cat fichier.txt
execve("/usr/bin/cat", ["cat", "fichier.txt"], 0x7ffc1e7b66f8 /* 31 vars */) = 0
brk(NULL)                               = 0x55c26eff1000
arch_prctl(0x3001 /* ARCH_??? */, 0x7fff68009ef0) = -1 EINVAL (Invalid argument)
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=13675, ...}) = 0
mmap(NULL, 13675, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fd5d8c4b000
close(3)                                = 0
openat(AT_FDCWD, "/lib64/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0p\0\4\0\0\0\0\0"..., 832) = 832
pread64(3, "\6\0\0\0\4\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0"..., 784, 64) = 784
pread64(3, "\4\0\0\0 \0\0\0\5\0\0\0GNU\0\2\0\0\300\4\0\0\0\3\0\0\0\0\0\0\0"..., 48, 848) = 48
pread64(3, "\4\0\0\0\24\0\0\0\3\0\0\0GNU\0\353|1\205uO9\255\311\361\31#\314\366T\354"..., 68, 896) = 68
fstat(3, {st_mode=S_IFREG|0755, st_size=2387008, ...}) = 0
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd5d8c49000
pread64(3, "\6\0\0\0\4\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0"..., 784, 64) = 784
mmap(NULL, 2133936, PROT_READ, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd5d8a00000
mprotect(0x7fd5d8a28000, 1892352, PROT_NONE) = 0
mmap(0x7fd5d8a28000, 1527808, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x28000) = 0x7fd5d8a28000
mmap(0x7fd5d8b9d000, 360448, PROT_READ, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x19d000) = 0x7fd5d8b9d000
mmap(0x7fd5d8bf6000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1f5000) = 0x7fd5d8bf6000
mmap(0x7fd5d8bfc000, 53168, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fd5d8bfc000
close(3)                                = 0
mmap(NULL, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd5d8c46000
arch_prctl(ARCH_SET_FS, 0x7fd5d8c46740) = 0
set_tid_address(0x7fd5d8c46a10)         = 12994
set_robust_list(0x7fd5d8c46a20, 24)     = 0
rseq(0x7fd5d8c470e0, 0x20, 0, 0x53053053) = 0
mprotect(0x7fd5d8bf6000, 16384, PROT_READ) = 0
mprotect(0x55c26daa9000, 4096, PROT_READ) = 0
mprotect(0x7fd5d8c83000, 8192, PROT_READ) = 0
prlimit64(0, RLIMIT_STACK, NULL, {rlim_cur=8192*1024, rlim_max=RLIM64_INFINITY}) = 0
munmap(0x7fd5d8c4b000, 13675)           = 0
getrandom("\x32\xb7\x76\x4f\x48\xe3\x3b\x71", 8, GRND_NONBLOCK) = 8
brk(NULL)                               = 0x55c26eff1000
brk(0x55c26f012000)                     = 0x55c26f012000
openat(AT_FDCWD, "/usr/lib/locale/locale-archive", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale/locale.alias", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=2998, ...}) = 0
read(3, "# Locale name alias data base.\n#"..., 4096) = 2998
read(3, "", 4096)                       = 0
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_IDENTIFICATION", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_IDENTIFICATION", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=369, ...}) = 0
mmap(NULL, 369, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fd5d8c82000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib64/gconv/gconv-modules.cache", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=26988, ...}) = 0
mmap(NULL, 26988, PROT_READ, MAP_SHARED, 3, 0) = 0x7fd5d8c3f000
close(3)                                = 0
futex(0x7fd5d8bfba6c, FUTEX_WAKE_PRIVATE, 2147483647) = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_MEASUREMENT", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_MEASUREMENT", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=23, ...}) = 0
mmap(NULL, 23, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fd5d8c4e000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_TELEPHONE", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_TELEPHONE", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=59, ...}) = 0
mmap(NULL, 59, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fd5d8c4d000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_ADDRESS", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_ADDRESS", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=167, ...}) = 0
mmap(NULL, 167, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fd5d8c4c000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_NAME", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_NAME", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=77, ...}) = 0
mmap(NULL, 77, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fd5d8c4b000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_PAPER", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_PAPER", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=34, ...}) = 0
mmap(NULL, 34, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fd5d8c3e000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_MESSAGES", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_MESSAGES", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFDIR|0755, st_size=29, ...}) = 0
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=57, ...}) = 0
mmap(NULL, 57, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fd5d8c3d000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_MONETARY", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_MONETARY", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=286, ...}) = 0
mmap(NULL, 286, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fd5d8c3c000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_COLLATE", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_COLLATE", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=2586930, ...}) = 0
mmap(NULL, 2586930, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fd5d8600000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_TIME", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_TIME", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=3284, ...}) = 0
mmap(NULL, 3284, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fd5d8c3b000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_NUMERIC", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_NUMERIC", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=54, ...}) = 0
mmap(NULL, 54, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fd5d8c3a000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_CTYPE", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_CTYPE", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=346132, ...}) = 0
mmap(NULL, 346132, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fd5d89ab000
close(3)                                = 0
fstat(1, {st_mode=S_IFCHR|0620, st_rdev=makedev(0x88, 0), ...}) = 0
openat(AT_FDCWD, "fichier.txt", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=8, ...}) = 0
fadvise64(3, 0, 0, POSIX_FADV_SEQUENTIAL) = 0
mmap(NULL, 139264, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd5d8c18000
read(3, "bonjour\n", 131072)            = 8
write(1, "bonjour\n", 8bonjour
)                = 8
read(3, "", 131072)                     = 0
munmap(0x7fd5d8c18000, 139264)          = 0
close(3)                                = 0
close(1)                                = 0
close(2)                                = 0
exit_group(0)                           = ?
+++ exited with 0 +++
```
- mettez en évidence le *syscall* qui demande l'ouverture du fichier en lecture
```
[dash@localhost ~]$ strace cat fichier.txt 2>&1 | grep -E 'open|openat'
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
openat(AT_FDCWD, "/lib64/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
openat(AT_FDCWD, "/usr/lib/locale/locale-archive", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale/locale.alias", O_RDONLY|O_CLOEXEC) = 3
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_IDENTIFICATION", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_IDENTIFICATION", O_RDONLY|O_CLOEXEC) = 3
openat(AT_FDCWD, "/usr/lib64/gconv/gconv-modules.cache", O_RDONLY) = 3
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_MEASUREMENT", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_MEASUREMENT", O_RDONLY|O_CLOEXEC) = 3
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_TELEPHONE", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_TELEPHONE", O_RDONLY|O_CLOEXEC) = 3
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_ADDRESS", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_ADDRESS", O_RDONLY|O_CLOEXEC) = 3
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_NAME", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_NAME", O_RDONLY|O_CLOEXEC) = 3
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_PAPER", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_PAPER", O_RDONLY|O_CLOEXEC) = 3
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_MESSAGES", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_MESSAGES", O_RDONLY|O_CLOEXEC) = 3
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES", O_RDONLY|O_CLOEXEC) = 3
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_MONETARY", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_MONETARY", O_RDONLY|O_CLOEXEC) = 3
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_COLLATE", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_COLLATE", O_RDONLY|O_CLOEXEC) = 3
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_TIME", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_TIME", O_RDONLY|O_CLOEXEC) = 3
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_NUMERIC", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_NUMERIC", O_RDONLY|O_CLOEXEC) = 3
openat(AT_FDCWD, "/usr/lib/locale/en_US.UTF-8/LC_CTYPE", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/en_US.utf8/LC_CTYPE", O_RDONLY|O_CLOEXEC) = 3
openat(AT_FDCWD, "fichier.txt", O_RDONLY) = 3
```
- mettez en évidence le *syscall* qui écrit le contenu du fichier dans le terminal
```
[dash@localhost ~]$ strace cat fichier.txt 2>&1 | grep -E 'write|writev'
write(1, "bonjour\n", 8bonjour
```

🌞 **Utiliser `strace` pour tracer l'exécution de `curl example.org`**

- vous devez utiliser une option de `strace`

- elle affiche juste un tableau qui liste tous les *syscalls*  appelés par la commande tracée, et combien de fois ils ont été appelé
```
[dash@localhost ~]$ strace cat fichier.txt 2>&1 | grep -E 'write|writev'
write(1, "bonjour\n", 8bonjour
[dash@localhost ~]$ strace -c curl example.org
<!doctype html>
<html>
<head>
    <title>Example Domain</title>

    <meta charset="utf-8" />
    <meta http-equiv="Content-type" content="text/html; charset=utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <style type="text/css">
    body {
        background-color: #f0f0f2;
        margin: 0;
        padding: 0;
        font-family: -apple-system, system-ui, BlinkMacSystemFont, "Segoe UI", "Open Sans", "Helvetica Neue", Helvetica, Arial, sans-serif;
        
    }
    div {
        width: 600px;
        margin: 5em auto;
        padding: 2em;
        background-color: #fdfdff;
        border-radius: 0.5em;
        box-shadow: 2px 3px 7px 2px rgba(0,0,0,0.02);
    }
    a:link, a:visited {
        color: #38488f;
        text-decoration: none;
    }
    @media (max-width: 700px) {
        div {
            margin: 0 auto;
            width: auto;
        }
    }
    </style>    
</head>

<body>
<div>
    <h1>Example Domain</h1>
    <p>This domain is for use in illustrative examples in documents. You may use this
    domain in literature without prior coordination or asking for permission.</p>
    <p><a href="https://www.iana.org/domains/example">More information...</a></p>
</div>
</body>
</html>
% time     seconds  usecs/call     calls    errors syscall
------ ----------- ----------- --------- --------- ----------------
 21.87    0.000821           5       141           mmap
 18.01    0.000676         676         1           execve
 14.68    0.000551          29        19           poll
  8.52    0.000320           5        60        14 openat
  7.96    0.000299         149         2           socket
  5.43    0.000204           5        36           read
  3.94    0.000148           2        54           close
  3.49    0.000131           3        37           mprotect
  2.82    0.000106           1        62           rt_sigaction
  2.82    0.000106         106         1         1 connect
  2.53    0.000095          47         2           newfstatat
  2.10    0.000079           1        46           fstat
  0.93    0.000035           1        24           futex
  0.85    0.000032          32         1           sendto
  0.69    0.000026          26         1           munmap
  0.59    0.000022          22         1           recvfrom
  0.48    0.000018           9         2           statfs
  0.40    0.000015           3         4           setsockopt
  0.37    0.000014           7         2         1 access
  0.29    0.000011           2         4           brk
  0.29    0.000011           2         4           pread64
  0.21    0.000008           8         1           pipe
  0.16    0.000006           1         6           fcntl
  0.13    0.000005           5         1           getpeername
  0.11    0.000004           2         2           getdents64
  0.08    0.000003           3         1           getsockname
  0.08    0.000003           3         1           prlimit64
  0.08    0.000003           3         1           getrandom
  0.05    0.000002           1         2         1 arch_prctl
  0.00    0.000000           0         7           write
  0.00    0.000000           0         3           rt_sigprocmask
  0.00    0.000000           0         2           ioctl
  0.00    0.000000           0         2           socketpair
  0.00    0.000000           0         1           getsockopt
  0.00    0.000000           0         1           sysinfo
  0.00    0.000000           0         1           set_tid_address
  0.00    0.000000           0         1           set_robust_list
  0.00    0.000000           0         1           rseq
  0.00    0.000000           0         1           clone3
------ ----------- ----------- --------- --------- ----------------
100.00    0.003754           6       539        17 total
```
## 2. sysdig

### A. Intro

`sysdig` est un outil qui permet de faire pleiiin de trucs, et notamment tracer les *syscalls*  que le kernel reçoit.

Si on le lance sans préciser, il affichera TOUS les *syscalls*  que reçoit votre kernel.

On peut ajouter des filtres, pour ne voir que les *syscalls*  qui nous intéressent.

Par exemple :

```bash
# si on veut tracer les *syscalls*  effectués par le programme echo
sysdig proc.name=echo
```

> Il existe des tonnes et des tonnes de champs utilisables pour les filtres, on peut consulter la liste avec `sysdig -l`.

Ensuite on le laisse tourner, et si un *syscall* est appelé et que ça matche notre filtre, il s'affichera !

Pour installer sysdig, utilisez les commandes suivantes (instructions pour Rocky Linux 9) :

```bash
# mettons complètement à jour l'OS d'abord si nécessaire
sudo dnf update -y 

# redémarrer pour charger la nouvelle version du kernel si besoin (c'est automatique, juste lance un reboot)
sudo reboot

# installer sysdig et ses dépendances
sudo dnf install -y epel-release
sudo dnf install -y dkms gcc kernel-devel make perl kernel-headers
curl -SLO https://github.com/draios/sysdig/releases/download/0.39.0/sysdig-0.39.0-x86_64.rpm
sudo rpm -ivh sysdig-0.39.0-x86_64.rpm
```

### B. Use it

🌞 **Utiliser `sysdig` pour tracer les *syscalls*  effectués par `ls`**

- faites `ls` sur un dossier qui contient des trucs (pas un dossier vide)
- mettez en évidence le *syscall* pour écrire dans le terminal le résultat du `ls`
```
[dash@localhost ~]$ sudo sysdig proc.name=ls > sys_ls.txt
[dash@localhost ~]$ cat sys_ls.txt | grep write
4444 18:13:42.345279386 0 ls (3281) > write fd=1(<f>/dev/tty1) size=66
4445 18:13:42.345301879 0 ls (3281) < write res=66 data=fichier.txt  .[0m.[01;31msysdig-0.39.0-x86_64.rpm.[0m  sys_ls.txt.
```

🌞 **Utiliser `sysdig` pour tracer les *syscalls*  effectués par `cat`**

- faites `cat` sur un fichier qui contient des trucs
```
[dash@localhost ~]$ sudo sysdig proc.name=cat > sys_cat.txt
```
- mettez en évidence le *syscall* qui demande l'ouverture du fichier en lecture
```
[dash@localhost ~]$ cat sys_cat.txt | grep open
2580 18:16:44.737859391 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/etc/ld.so.cache flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2581 18:16:44.737866394 0 cat (3293) < openat fd=3(<f>/etc/ld.so.cache) dirfd=-100(AT_FDCWD) name=/etc/ld.so.cache flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=FD00 ino=8520837
2588 18:16:44.737883266 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/lib64/libc.so.6 flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2589 18:16:44.737890770 0 cat (3293) < openat fd=3(<f>/lib64/libc.so.6) dirfd=-100(AT_FDCWD) name=/lib64/libc.so.6 flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=FD00 ino=13405143
2642 18:16:44.738167904 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=<NA> flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2643 18:16:44.738178073 0 cat (3293) < openat fd=-2(ENOENT) dirfd=-100(AT_FDCWD) name=/usr/lib/locale/locale-archive flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=0 ino=0
2644 18:16:44.738186108 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/share/locale/locale.alias flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2645 18:16:44.738192751 0 cat (3293) < openat fd=3(<f>/usr/share/locale/locale.alias) dirfd=-100(AT_FDCWD) name=/usr/share/locale/locale.alias flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=FD00 ino=4593334
2654 18:16:44.738222026 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.UTF-8/LC_IDENTIFICATION flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2655 18:16:44.738226173 0 cat (3293) < openat fd=-2(ENOENT) dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.UTF-8/LC_IDENTIFICATION flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=0 ino=0
2656 18:16:44.738227997 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.utf8/LC_IDENTIFICATION flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2657 18:16:44.738232996 0 cat (3293) < openat fd=3(<f>/usr/lib/locale/en_US.utf8/LC_IDENTIFICATION) dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.utf8/LC_IDENTIFICATION flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=FD00 ino=295652
2664 18:16:44.738246502 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/lib64/gconv/gconv-modules.cache flags=1(O_RDONLY) mode=0
2665 18:16:44.738251762 0 cat (3293) < openat fd=3(<f>/usr/lib64/gconv/gconv-modules.cache) dirfd=-100(AT_FDCWD) name=/usr/lib64/gconv/gconv-modules.cache flags=1(O_RDONLY) mode=0 dev=FD00 ino=4593280
2674 18:16:44.738268613 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.UTF-8/LC_MEASUREMENT flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2675 18:16:44.738272541 0 cat (3293) < openat fd=-2(ENOENT) dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.UTF-8/LC_MEASUREMENT flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=0 ino=0
2676 18:16:44.738274394 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.utf8/LC_MEASUREMENT flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2677 18:16:44.738278742 0 cat (3293) < openat fd=3(<f>/usr/lib/locale/en_US.utf8/LC_MEASUREMENT) dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.utf8/LC_MEASUREMENT flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=FD00 ino=295653
2684 18:16:44.738291126 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.UTF-8/LC_TELEPHONE flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2685 18:16:44.738294672 0 cat (3293) < openat fd=-2(ENOENT) dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.UTF-8/LC_TELEPHONE flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=0 ino=0
2686 18:16:44.738296386 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.utf8/LC_TELEPHONE flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2687 18:16:44.738300884 0 cat (3293) < openat fd=3(<f>/usr/lib/locale/en_US.utf8/LC_TELEPHONE) dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.utf8/LC_TELEPHONE flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=FD00 ino=295655
2694 18:16:44.738311805 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.UTF-8/LC_ADDRESS flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2695 18:16:44.738315481 0 cat (3293) < openat fd=-2(ENOENT) dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.UTF-8/LC_ADDRESS flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=0 ino=0
2696 18:16:44.738317094 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.utf8/LC_ADDRESS flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2697 18:16:44.738322294 0 cat (3293) < openat fd=3(<f>/usr/lib/locale/en_US.utf8/LC_ADDRESS) dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.utf8/LC_ADDRESS flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=FD00 ino=295650
2704 18:16:44.738333175 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.UTF-8/LC_NAME flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2705 18:16:44.738337032 0 cat (3293) < openat fd=-2(ENOENT) dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.UTF-8/LC_NAME flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=0 ino=0
2706 18:16:44.738338585 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.utf8/LC_NAME flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2707 18:16:44.738342703 0 cat (3293) < openat fd=3(<f>/usr/lib/locale/en_US.utf8/LC_NAME) dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.utf8/LC_NAME flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=FD00 ino=13405126
2714 18:16:44.738353413 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.UTF-8/LC_PAPER flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2715 18:16:44.738356699 0 cat (3293) < openat fd=-2(ENOENT) dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.UTF-8/LC_PAPER flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=0 ino=0
2716 18:16:44.738358322 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.utf8/LC_PAPER flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2717 18:16:44.738362650 0 cat (3293) < openat fd=3(<f>/usr/lib/locale/en_US.utf8/LC_PAPER) dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.utf8/LC_PAPER flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=FD00 ino=8563523
2724 18:16:44.738401962 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.UTF-8/LC_MESSAGES flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2725 18:16:44.738423165 0 cat (3293) < openat fd=-2(ENOENT) dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.UTF-8/LC_MESSAGES flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=0 ino=0
2726 18:16:44.738425850 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.utf8/LC_MESSAGES flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2727 18:16:44.738431570 0 cat (3293) < openat fd=3(<f>/usr/lib/locale/en_US.utf8/LC_MESSAGES) dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.utf8/LC_MESSAGES flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=FD00 ino=4599007
2732 18:16:44.738436029 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2733 18:16:44.738440918 0 cat (3293) < openat fd=3(<f>/usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES) dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=FD00 ino=295664
2740 18:16:44.738454794 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.UTF-8/LC_MONETARY flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2741 18:16:44.738458070 0 cat (3293) < openat fd=-2(ENOENT) dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.UTF-8/LC_MONETARY flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=0 ino=0
2742 18:16:44.738459703 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.utf8/LC_MONETARY flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2743 18:16:44.738464162 0 cat (3293) < openat fd=3(<f>/usr/lib/locale/en_US.utf8/LC_MONETARY) dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.utf8/LC_MONETARY flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=FD00 ino=295654
2750 18:16:44.738475744 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.UTF-8/LC_COLLATE flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2751 18:16:44.738479090 0 cat (3293) < openat fd=-2(ENOENT) dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.UTF-8/LC_COLLATE flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=0 ino=0
2752 18:16:44.738480743 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.utf8/LC_COLLATE flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2753 18:16:44.738485342 0 cat (3293) < openat fd=3(<f>/usr/lib/locale/en_US.utf8/LC_COLLATE) dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.utf8/LC_COLLATE flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=FD00 ino=13405124
2760 18:16:44.738507273 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.UTF-8/LC_TIME flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2761 18:16:44.738510559 0 cat (3293) < openat fd=-2(ENOENT) dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.UTF-8/LC_TIME flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=0 ino=0
2762 18:16:44.738512182 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.utf8/LC_TIME flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2763 18:16:44.738516931 0 cat (3293) < openat fd=3(<f>/usr/lib/locale/en_US.utf8/LC_TIME) dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.utf8/LC_TIME flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=FD00 ino=295656
2770 18:16:44.738530597 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.UTF-8/LC_NUMERIC flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2771 18:16:44.738534694 0 cat (3293) < openat fd=-2(ENOENT) dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.UTF-8/LC_NUMERIC flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=0 ino=0
2772 18:16:44.738536388 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.utf8/LC_NUMERIC flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2773 18:16:44.738540676 0 cat (3293) < openat fd=3(<f>/usr/lib/locale/en_US.utf8/LC_NUMERIC) dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.utf8/LC_NUMERIC flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=FD00 ino=13405127
2780 18:16:44.738555123 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.UTF-8/LC_CTYPE flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2781 18:16:44.738558369 0 cat (3293) < openat fd=-2(ENOENT) dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.UTF-8/LC_CTYPE flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=0 ino=0
2782 18:16:44.738559992 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.utf8/LC_CTYPE flags=4097(O_RDONLY|O_CLOEXEC) mode=0
2783 18:16:44.738570482 0 cat (3293) < openat fd=3(<f>/usr/lib/locale/en_US.utf8/LC_CTYPE) dirfd=-100(AT_FDCWD) name=/usr/lib/locale/en_US.utf8/LC_CTYPE flags=4097(O_RDONLY|O_CLOEXEC) mode=0 dev=FD00 ino=4593603
2792 18:16:44.738596210 0 cat (3293) > openat dirfd=-100(AT_FDCWD) name=fichier.txt(/home/dash/fichier.txt) flags=1(O_RDONLY) mode=0
2793 18:16:44.738601971 0 cat (3293) < openat fd=3(<f>/home/dash/fichier.txt) dirfd=-100(AT_FDCWD) name=fichier.txt(/home/dash/fichier.txt) flags=1(O_RDONLY) mode=0 dev=FD00 ino=5226332
```
- mettez en évidence le *syscall* qui écrit le contenu du fichier dans le terminal
```
[dash@localhost ~]$ cat sys_cat.txt | grep write
3130 18:16:44.739975900 0 cat (3293) > write fd=1(<f>/dev/tty1) size=8
3131 18:16:44.739989536 0 cat (3293) < write res=8 data=bonjour.
```

🌞 **Utiliser `sysdig` pour tracer les *syscalls*  effectués par votre utilisateur**

```
[dash@localhost ~]$ sudo sysdig user.name=$USER
```


🌞 **Livrez le fichier `curl.scap` dans le dépôt git de rendu**

- `sysdig` permet d'enregistrer ce qu'il capture dans un fichier pour analyse ultérieure
- l'extension c'est `.scap` par convention
- **capturez les *syscalls*  effectués par un `curl example.org`**  
[curl.scap](curl.scap)


