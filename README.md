SElinux

3 способа включения по не стндартному порту
1-setsebool
2-ports_ne_standart
3-install_modulSELinux


Причина неработоспособности механизма обновления  в том что Selinux заблокировал доступ к обновлению файлов динамического обновления для DNS сервера в каталоге /etc/named/dynamic.

Нужно изменить контекст  файлов, к которым DNS серверу затруднен доступ командами semanage fcontext -a -t named_zone_t /etc/named/dynamic и затем выполнить запись контекста в ядро restorecon -v /etc/named/dynamic. 
В данном случае приведены примеры для каталога dynamic, в данный каталог DNS сервер записывает динамические обновления от DNS клиентов.
В файле playbook.yml изменяется контекст файлов.
