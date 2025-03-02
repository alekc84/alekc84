смотрим текущую версию  ядра 
ecss@ecss:~$ uname -r
4.15.0-213-generic
ecss@ecss:~$

смотрим какая архитектура процессора
root@ecss:~# uname -p
x86_64

создаем каталог, в него загружаем пакеты для обновления ядра
root@ecss:~/kernel# ls -la
total 219632
drwxr-xr-x 2 root root      4096 Mar  2 14:14 .
drwxr-xr-x 8 ecss ecss      4096 Mar  2 14:04 ..
-rw-r--r-- 1 root root  13870320 Feb 22 01:24 linux-headers-6.13.4-061304_6.13.4-061304.202502211345_all.deb
-rw-r--r-- 1 root root   3833574 Feb 22 01:23 linux-headers-6.13.4-061304-generic_6.13.4-061304.202502211345_amd64.deb
-rw-r--r-- 1 root root  15872192 Feb 22 01:23 linux-image-unsigned-6.13.4-061304-generic_6.13.4-061304.202502211345_amd64.deb
-rw-r--r-- 1 root root 191303872 Feb 22 01:23 linux-modules-6.13.4-061304-generic_6.13.4-061304.202502211345_amd64.deb
root@ecss:~/kernel#
root@ecss:~/kernel#
проеряем , что в списке есть новое ядро 
root@ecss:~/kernel# ls -al /boot
total 117980
drwxr-xr-x  4 root root     4096 Mar  2 14:17 .
drwxr-xr-x 24 root root     4096 Mar  2 14:17 ..
-rw-r--r--  1 root root   217558 Jun 16  2023 config-4.15.0-213-generic
-rw-r--r--  1 root root   310783 Feb 21 13:45 config-6.13.4-061304-generic
drwxr-xr-x  5 root root     4096 Mar  2 14:17 grub
-rw-r--r--  1 root root 63116261 Feb 28 18:21 initrd.img-4.15.0-213-generic
-rw-r--r--  1 root root 18663104 Mar  2 14:17 initrd.img-6.13.4-061304-generic
drwx------  2 root root    16384 Feb 28 18:14 lost+found
-rw-------  1 root root  4080574 Jun 16  2023 System.map-4.15.0-213-generic
-rw-------  1 root root 10067090 Feb 21 13:45 System.map-6.13.4-061304-generic
-rw-------  1 root root  8470184 Jun 16  2023 vmlinuz-4.15.0-213-generic
-rw-------  1 root root 15839744 Feb 21 13:45 vmlinuz-6.13.4-061304-generic
root@ecss:~/kernel#    



обновляем конфигурацию загрузчика 
root@ecss:~/kernel# sudo update-grub
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.13.4-061304-generic
Found initrd image: /boot/initrd.img-6.13.4-061304-generic
Found linux image: /boot/vmlinuz-4.15.0-213-generic
Found initrd image: /boot/initrd.img-4.15.0-213-generic
done
root@ecss:~/kernel#


root@ecss:~/kernel# sudo grub-set-default 0
Searching for GRUB installation directory ... found: /boot/grub
root@ecss:~/kernel#
