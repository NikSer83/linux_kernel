## Домашнее задание на тему "Обновление ядра Linux"
1. Запустить ВМ c Ubuntu.
2. Обновите ядро ОС на новейшую стабильную версию из mainline-репозитория.
3. Оформите отчет в README-файле в GitHub-репозитории.

Для выполнения задания мной использовались: гипервизор VirtualBox и ОС Ubuntu server 24.04.5 LTS

Вывод информации о ядре:
```
nikser@linuxkernel:~$ uname -r
6.8.0-146-generic
```
Создаю директорию в которую буду скачивать новое ядро:
```
nikser@linuxkernel:~$ mkdir kernel && cd kernel
```
Затем скачиваю новое ядро с **https://kernel.ubuntu.com/mainline**
Выбрал ядро 7.0.0
```
nikser@linuxkernel:~/kernel$ wget https://kernel.ubuntu.com/mainline/v7.0/amd64/linux-headers-7.0.0-070000-generic_7.0.0-070000.202604122140_amd64.deb

nikser@linuxkernel:~/kernel$ wget https://kernel.ubuntu.com/mainline/v7.0/amd64/linux-headers-7.0.0-070000_7.0.0-070000.202604122140_all.deb

nikser@linuxkernel:~/kernel$ wget https://kernel.ubuntu.com/mainline/v7.0/amd64/linux-image-unsigned-7.0.0-070000-generic_7.0.0-070000.202604122140_amd64.deb

nikser@linuxkernel:~/kernel$ wget https://kernel.ubuntu.com/mainline/v7.0/amd64/linux-modules-7.0.0-070000-generic_7.0.0-070000.202604122140_amd64.deb
```
Устанавливаю скачанные пакеты
```
nikser@linuxkernel:~/kernel$  sudo dpkg -i *.deb
```
Проверяю наличие нового ядра в /boot
```
nikser@linuxkernel:~/kernel$ ls -al /boot
total 220320
drwxr-xr-x  4 root root     4096 окт  1 17:52 .
drwxr-xr-x 23 root root     4096 сен 30 17:18 ..
-rw-r--r--  1 root root   287560 сен  3 14:47 config-6.8.0-146-generic
-rw-r--r--  1 root root   307839 апр 12 21:40 config-7.0.0-070000-generic
drwxr-xr-x  5 root root     4096 окт  1 17:53 grub
lrwxrwxrwx  1 root root       31 окт  1 17:52 initrd.img -> initrd.img-7.0.0-070000-generic
-rw-r--r--  1 root root 76558081 сен 30 17:19 initrd.img-6.8.0-146-generic
-rw-r--r--  1 root root 83696213 окт  1 17:52 initrd.img-7.0.0-070000-generic
lrwxrwxrwx  1 root root       28 сен 30 17:18 initrd.img.old -> initrd.img-6.8.0-146-generic
drwx------  2 root root    16384 сен 30 17:10 lost+found
-rw-------  1 root root  9136419 сен  3 14:47 System.map-6.8.0-146-generic
-rw-------  1 root root 10982829 апр 12 21:40 System.map-7.0.0-070000-generic
lrwxrwxrwx  1 root root       28 окт  1 17:52 vmlinuz -> vmlinuz-7.0.0-070000-generic
-rw-------  1 root root 15067528 сен  3 14:49 vmlinuz-6.8.0-146-generic
-rw-------  1 root root 17248768 апр 12 21:40 vmlinuz-7.0.0-070000-generic
lrwxrwxrwx  1 root root       25 сен 30 17:18 vmlinuz.old -> vmlinuz-6.8.0-146-generic
```
Перезагружаю систему:
```
nikser@linuxkernel:~/kernel$ sudo reboot
```
Проверяю версию ядра:
```
nikser@linuxkernel:~$ uname -r
7.0.0-070000-generic
```
