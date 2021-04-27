# OC
Лабораторная работа №3  
Номер группы: 728111  
Номер зачетки: 1800189
## В своей виртуальной машине сделать:
1. создать нового пользователя [ваша фамилия2] (скриншот хэшов паролей в отчет)  
`sudo useradd khisamov`  
`sudo passwd khisamov`  
`sudo cat /etc/shadow`  
2. изменить настройки пользователя: домашний каталог, дату окончания действия учетной записи (скриншот в отчет)  
`sudo usermod -d /home/khisamov -e 2021-12-31 khisamov`  
`sudo chage -l khisamov`  
3. создать новую группу [номер вашей группы]  
`sudo groupadd 728111`  
`sudo cat /etc/group`  
4. перевести созданного пользователя в эту группу (скриншот таблицы в отчет)  
Войти в рут  
`adduser khisamov 728111 && newgrp 728111`  
5. установить для данного пользователя квоты на  разделе EXT2  (мягкая квота=последние 2 числа в номер зачетки (Мбайт), жесткая=2x"последние 2 числа в номер зачетки" (Мбайт)) (скриншоты в отчет)  
`sudo nano /etc/fstab`  
`UUID=iduser /mnt/khisamov/ext2 ext2 usrquota 0 2`  
`Ctrl + O`  
`Ctrl + X`  
`sudo mount -o remount /mnt/khisamov/ext2/`  
`mount | grep quota`  
`sudo quotacheck -fam`  
`sudo quotaon -a`  
`sudo edquota -u khisamov`  
6. вывести таблицу квот (скриншот таблицы в отчет)  
`sudo repquota -vs /mnt/khisamov/ext2`  
## Что надо изучить
1. дискреционное управление доступом
2. матрица доступа
3. группы
4. ХЕШ пароля (показать)
5. жесткие и мягкие квоты
