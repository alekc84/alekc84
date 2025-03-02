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


новая ubuntu 22.04.
ecss@ecss:~$ uname -r
5.15.0-133-generic

ecss@ecss:~$ ls -al /boot
total 121388
drwxr-xr-x  4 root root      4096 Mar  2 15:02 .
drwxr-xr-x 20 root root      4096 Mar  2 15:02 ..
-rw-------  1 root root   6295053 Feb  7 17:44 System.map-5.15.0-133-generic
-rw-r--r--  1 root root    262228 Feb  7 17:44 config-5.15.0-133-generic
drwxr-xr-x  5 root root      4096 Mar  2 15:02 grub
lrwxrwxrwx  1 root root        29 Mar  2 15:02 initrd.img -> initrd.img-5.15.0-133-generic
-rw-r--r--  1 root root 105995865 Mar  2 15:02 initrd.img-5.15.0-133-generic
lrwxrwxrwx  1 root root        29 Mar  2 15:02 initrd.img.old -> initrd.img-5.15.0-133-generic
drwx------  2 root root     16384 Mar  2 15:00 lost+found
lrwxrwxrwx  1 root root        26 Mar  2 15:02 vmlinuz -> vmlinuz-5.15.0-133-generic
-rw-------  1 root root  11711400 Feb  7 18:12 vmlinuz-5.15.0-133-generic
lrwxrwxrwx  1 root root        26 Mar  2 15:02 vmlinuz.old -> vmlinuz-5.15.0-133-generic
ecss@ecss:~$
drwxrwxr-x 2 ecss ecss      4096 Mar  2 15:19 .
drwxr-x--- 5 ecss ecss      4096 Mar  2 15:13 ..
-rw-rw-r-- 1 ecss ecss   3812282 Feb  8 09:32 linux-headers-6.13.0-061300-generic_6.13.0-061300.202501302155_amd64.deb
-rw-rw-r-- 1 ecss ecss  13868606 Feb  8 09:32 linux-headers-6.13.0-061300_6.13.0-061300.202501302155_all.deb
-rw-rw-r-- 1 ecss ecss  15861952 Feb  8 09:32 linux-image-unsigned-6.13.0-061300-generic_6.13.0-061300.202501302155_amd64.deb
-rw-rw-r-- 1 ecss ecss 191856832 Feb  8 09:32 linux-modules-6.13.0-061300-generic_6.13.0-061300.202501302155_amd64.deb
ecss@ecss:~/kernel$ sudo dpkg -i *.deb


ecss@ecss:~$ uname -r
6.13.0-061300-generic
ecss@ecss:~$
ecss@ecss:~$



