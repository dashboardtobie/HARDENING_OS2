# Part I : Learn

## 1. Anatomy of a program

### A. `file`

🌞 **Utiliser `file` pour déterminer le type de :**

- la commande `ls`
```
[dash@localhost ~]$ file /usr/bin/ls
/usr/bin/ls: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=fe37adecca22a782c4fb274ae601f220cc1fbb4d, for GNU/Linux 3.2.0, stripped
```
- la commande `ip`
```
[dash@localhost ~]$ file /usr/sbin/ip
/usr/sbin/ip: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=77a2f5899f0529f27d87bb29c6b84c535739e1c7, for GNU/Linux 3.2.0, stripped
```
- un fichier `.mp3` que vous aurez téléchargé sur le disque de la VM
```
dash@localhost ~]$ sudo file /root/DamsoBruxellesVie.mp3
/root/DamsoBruxellesVie.mp3: Audio file with ID3 version 2.4.0, contains:MPEG ADTS, layer III, v1, 320 kbps, 44.1 kHz, Stereo
```

### B. `readelf`

🌞 **Utiliser `readelf` sur le programme `ls`**

- afficher le *header* du programme
```
[dash@localhost ~]$ readelf -h /usr/bin/ls
ELF Header:
  Magic:   7f 45 4c 46 02 01 01 00 00 00 00 00 00 00 00 00 
  Class:                             ELF64
  Data:                              2's complement, little endian
  Version:                           1 (current)
  OS/ABI:                            UNIX - System V
  ABI Version:                       0
  Type:                              DYN (Shared object file)
  Machine:                           Advanced Micro Devices X86-64
  Version:                           0x1
  Entry point address:               0x6b10
  Start of program headers:          64 (bytes into file)
  Start of section headers:          138952 (bytes into file)
  Flags:                             0x0
  Size of this header:               64 (bytes)
  Size of program headers:           56 (bytes)
  Number of program headers:         13
  Size of section headers:           64 (bytes)
  Number of section headers:         30
  Section header string table index: 29
```
- afficher la liste des sections du programme
```
[dash@localhost ~]$ readelf -S /usr/bin/ls
There are 30 section headers, starting at offset 0x21ec8:

Section Headers:
  [Nr] Name              Type             Address           Offset
       Size              EntSize          Flags  Link  Info  Align
  [ 0]                   NULL             0000000000000000  00000000
       0000000000000000  0000000000000000           0     0     0
  [ 1] .interp           PROGBITS         0000000000000318  00000318
       000000000000001c  0000000000000000   A       0     0     1
  [ 2] .note.gnu.pr[...] NOTE             0000000000000338  00000338
       0000000000000030  0000000000000000   A       0     0     8
  [ 3] .note.gnu.bu[...] NOTE             0000000000000368  00000368
       0000000000000024  0000000000000000   A       0     0     4
  [ 4] .note.ABI-tag     NOTE             000000000000038c  0000038c
       0000000000000020  0000000000000000   A       0     0     4
  [ 5] .gnu.hash         GNU_HASH         00000000000003b0  000003b0
       0000000000000040  0000000000000000   A       6     0     8
  [ 6] .dynsym           DYNSYM           00000000000003f0  000003f0
       0000000000000bb8  0000000000000018   A       7     1     8
  [ 7] .dynstr           STRTAB           0000000000000fa8  00000fa8
       00000000000005c5  0000000000000000   A       0     0     1
  [ 8] .gnu.version      VERSYM           000000000000156e  0000156e
       00000000000000fa  0000000000000002   A       6     0     2
  [ 9] .gnu.version_r    VERNEED          0000000000001668  00001668
       00000000000000c0  0000000000000000   A       7     2     8
  [10] .rela.dyn         RELA             0000000000001728  00001728
       0000000000001410  0000000000000018   A       6     0     8
  [11] .rela.plt         RELA             0000000000002b38  00002b38
       00000000000009d8  0000000000000018  AI       6    24     8
  [12] .init             PROGBITS         0000000000004000  00004000
       000000000000001b  0000000000000000  AX       0     0     4
  [13] .plt              PROGBITS         0000000000004020  00004020
       00000000000006a0  0000000000000010  AX       0     0     16
  [14] .plt.sec          PROGBITS         00000000000046c0  000046c0
       0000000000000690  0000000000000010  AX       0     0     16
  [15] .text             PROGBITS         0000000000004d50  00004d50
       0000000000012532  0000000000000000  AX       0     0     16
  [16] .fini             PROGBITS         0000000000017284  00017284
       000000000000000d  0000000000000000  AX       0     0     4
  [17] .rodata           PROGBITS         0000000000018000  00018000
       0000000000004dec  0000000000000000   A       0     0     32
  [18] .eh_frame_hdr     PROGBITS         000000000001cdec  0001cdec
       000000000000056c  0000000000000000   A       0     0     4
  [19] .eh_frame         PROGBITS         000000000001d358  0001d358
       0000000000002128  0000000000000000   A       0     0     8
  [20] .init_array       INIT_ARRAY       0000000000020f70  0001ff70
       0000000000000008  0000000000000008  WA       0     0     8
  [21] .fini_array       FINI_ARRAY       0000000000020f78  0001ff78
       0000000000000008  0000000000000008  WA       0     0     8
  [22] .data.rel.ro      PROGBITS         0000000000020f80  0001ff80
       0000000000000a98  0000000000000000  WA       0     0     32
  [23] .dynamic          DYNAMIC          0000000000021a18  00020a18
       0000000000000210  0000000000000010  WA       7     0     8
  [24] .got              PROGBITS         0000000000021c28  00020c28
       00000000000003c8  0000000000000008  WA       0     0     8
  [25] .data             PROGBITS         0000000000022000  00021000
       0000000000000278  0000000000000000  WA       0     0     32
  [26] .bss              NOBITS           0000000000022280  00021278
       00000000000012c0  0000000000000000  WA       0     0     32
  [27] .gnu_debuglink    PROGBITS         0000000000000000  00021278
       0000000000000020  0000000000000000           0     0     4
  [28] .gnu_debugdata    PROGBITS         0000000000000000  00021298
       0000000000000b08  0000000000000000           0     0     1
  [29] .shstrtab         STRTAB           0000000000000000  00021da0
       0000000000000128  0000000000000000           0     0     1
Key to Flags:
  W (write), A (alloc), X (execute), M (merge), S (strings), I (info),
  L (link order), O (extra OS processing required), G (group), T (TLS),
  C (compressed), x (unknown), o (OS specific), E (exclude),
  l (large), p (processor specific)
```
- déterminer à quel adresse commence le code du programme
  - pour rappel, le code est dans la section `.text`
```
[dash@localhost ~]$ readelf -S /usr/bin/ls | grep .text
  [15] .text             PROGBITS         0000000000004d50  00004d50
```
Le code du programme commence à l'adresse `0000000000004d50`

### C. `ldd`

`ldd` est un outil qui permet de manipuler le *dynamic linker* de Linux. Le *dynamic linker* c'est un programme qui s'occupe de trouver les librairies nécessaires quand un autre programme se lance.

🌞 **Utiliser `ldd` sur le programme `ls`**

- afficher la liste des librairies que va utiliser `ls` pendant son fonctionnement
```
[dash@localhost ~]$ ldd /usr/bin/ls
	linux-vdso.so.1 (0x00007ffe89d5e000)
	libselinux.so.1 => /lib64/libselinux.so.1 (0x00007f2c09949000)
	libcap.so.2 => /lib64/libcap.so.2 (0x00007f2c0993f000)
	libc.so.6 => /lib64/libc.so.6 (0x00007f2c09600000)
	libpcre2-8.so.0 => /lib64/libpcre2-8.so.0 (0x00007f2c098a3000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f2c099a0000)
```
- déterminer, parmi ces librairies, laquelle est la Glibc
La Glibc c'est `libc.so.6 => /lib64/libc.so.6`


## 2. Syscalls basics

### A. Syscall list


🌞 **Donner le nom ET l'identifiant unique d'un syscall qui permet à un processus de...**

- lire un fichier stocké sur disque
Nom:`read` ; Id:`0`
- écrire dans un fichier stocké sur disque
Nom:`write` ; Id:`1`
- lancer un nouveau processus
Nom:`clone` ; Id:`56`

### B. `objdump`

`objdump` permet de désassembler un programme, c'est à dire d'afficher le code contenu par un exécutable, sous forme de langage assembleur compréhensible par les humains (un peu, beaucoup plus qu'une purée d'octets en tout cas !)

🌞 **Utiliser `objdump`** sur la commande `ls`

- afficher le contenu de la section `.text`
```
[dash@localhost ~]$ objdump -d -j .text /usr/bin/ls | head -10

/usr/bin/ls:     file format elf64-x86-64


Disassembly of section .text:

0000000000004d50 <_obstack_begin@@Base-0xb090>:
    4d50:	50                   	push   %rax
    4d51:	e8 da f9 ff ff       	callq  4730 <abort@plt>
    4d56:	e8 d5 f9 ff ff       	callq  4730 <abort@plt>
[dash@localhost ~]$ objdump -d -j .text /usr/bin/ls | head -20

/usr/bin/ls:     file format elf64-x86-64


Disassembly of section .text:

0000000000004d50 <_obstack_begin@@Base-0xb090>:
    4d50:	50                   	push   %rax
    4d51:	e8 da f9 ff ff       	callq  4730 <abort@plt>
    4d56:	e8 d5 f9 ff ff       	callq  4730 <abort@plt>
    4d5b:	e8 d0 f9 ff ff       	callq  4730 <abort@plt>
    4d60:	e8 cb f9 ff ff       	callq  4730 <abort@plt>
    4d65:	e8 c6 f9 ff ff       	callq  4730 <abort@plt>
    4d6a:	e8 c1 f9 ff ff       	callq  4730 <abort@plt>
    4d6f:	e8 bc f9 ff ff       	callq  4730 <abort@plt>
    4d74:	e8 b7 f9 ff ff       	callq  4730 <abort@plt>
    4d79:	e8 b2 f9 ff ff       	callq  4730 <abort@plt>
    4d7e:	66 90                	xchg   %ax,%ax
    4d80:	f3 0f 1e fa          	endbr64 
    4d84:	41 57                	push   %r15

<snip>
```

- mettez en évidence quelques lignes qui contiennent l'instruction `call`
```
dash@localhost ~]$ objdump -d -j .text /usr/bin/ls | grep -i 'call' | head - 20
==> standard input <==
    4d51:	e8 da f9 ff ff       	callq  4730 <abort@plt>
    4d56:	e8 d5 f9 ff ff       	callq  4730 <abort@plt>
    4d5b:	e8 d0 f9 ff ff       	callq  4730 <abort@plt>
    4d60:	e8 cb f9 ff ff       	callq  4730 <abort@plt>
    4d65:	e8 c6 f9 ff ff       	callq  4730 <abort@plt>
    4d6a:	e8 c1 f9 ff ff       	callq  4730 <abort@plt>
    4d6f:	e8 bc f9 ff ff       	callq  4730 <abort@plt>
    4d74:	e8 b7 f9 ff ff       	callq  4730 <abort@plt>
    4d79:	e8 b2 f9 ff ff       	callq  4730 <abort@plt>
    4dbc:	e8 6f fb ff ff       	callq  4930 <strrchr@plt>

<snip>
```
- mettez en évidence quelques lignes qui contiennent l'instruction `syscall`
```
[dash@localhost ~]$ objdump -d -j .text /usr/bin/ls | grep -i 'syscall'
[dash@localhost ~]$ 
```

🌞 **Utiliser `objdump`** sur la librairie Glibc

- mettez en évidence quelques lignes qui contiennent l'instruction `syscall`
```
[dash@localhost ~]$ objdump -d /lib64/libc.so.6 | grep 'syscall' | head -20
   29769:	0f 05                	syscall 
   29799:	0f 05                	syscall 
   29843:	0f 05                	syscall 
   298af:	0f 05                	syscall 
   298ee:	0f 05                	syscall 
   29abf:	0f 05                	syscall 
   29b32:	0f 05                	syscall 
   2a31b:	0f 05                	syscall 
   3e369:	0f 05                	syscall 
   3e399:	0f 05                	syscall 
   3e3ca:	0f 05                	syscall 
   3e409:	0f 05                	syscall 
   3e439:	0f 05                	syscall 
   3e449:	0f 05                	syscall 
   3e459:	0f 05                	syscall 
   3e469:	0f 05                	syscall 
   3e479:	0f 05                	syscall 
   3e489:	0f 05                	syscall 
   3e499:	0f 05                	syscall 
   3e4c9:	0f 05                	syscall
--
```
- trouvez l'instrution `syscall` qui exécute le syscall `close()`

```
[dash@localhost ~]$ objdump -d /lib64/libc.so.6 | grep -B2 'syscall' | grep '$0x3' -A3
<snip>

--
  167946:	b8 03 00 00 00       	mov    $0x3,%eax
  16794b:	0f 05                	syscall 
--
  167a00:	8b 3b                	mov    (%rbx),%edi
  167a02:	b8 03 00 00 00       	mov    $0x3,%eax
  167a07:	0f 05                	syscall 
--
  167bd5:	b8 03 00 00 00       	mov    $0x3,%eax
  167bda:	8b 7d a0             	mov    -0x60(%rbp),%edi
  167bdd:	0f 05                	syscall 
--
```

