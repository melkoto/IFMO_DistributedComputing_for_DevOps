# IFMO_DistributedComputing_for_DevOps
Distributed Computing course for DevOps 2025

## IP 
```bash
ssh -l ubuntu 51.250.45.157
```

## Запуск контейнеров через Ansible
```bash
~/Local/masters/2-semester/rasp_sistem/IFMO_DistributedComputing_for_DevOps/ansible git:[main]
ansible-playbook -i inventory.ini playbook.yml

PLAY [Развёртывание WordPress на удалённом сервере] ************************************************************************************************************************************************************************************************************************************************************************************************

TASK [Gathering Facts] *****************************************************************************************************************************************************************************************************************************************************************************************************************************
[WARNING]: Platform linux on host 51.250.45.157 is using the discovered Python interpreter at /usr/bin/python3.12, but future installation of another Python interpreter could change the meaning of that path. See https://docs.ansible.com/ansible-core/2.18/reference_appendices/interpreter_discovery.html for more information.
ok: [51.250.45.157]

TASK [wordpress : Вывести значение переменной HOME] ************************************************************************************************************************************************************************************************************************************************************************************************
ok: [51.250.45.157] => {
    "msg": "Домашняя директория: /root"
}

TASK [wordpress : Обновить apt-кэш] ****************************************************************************************************************************************************************************************************************************************************************************************************************
changed: [51.250.45.157]

TASK [wordpress : Добавить GPG-ключ официального репозитория Docker] *******************************************************************************************************************************************************************************************************************************************************************************
ok: [51.250.45.157]

TASK [wordpress : Добавить официальный репозиторий Docker] *****************************************************************************************************************************************************************************************************************************************************************************************
ok: [51.250.45.157]

TASK [wordpress : Обновить apt-кэш с новым репозиторием Docker] ************************************************************************************************************************************************************************************************************************************************************************************
changed: [51.250.45.157]

TASK [wordpress : Установить Docker CE, Docker CE CLI, containerd и Compose Plugin] ****************************************************************************************************************************************************************************************************************************************************************
ok: [51.250.45.157]

TASK [wordpress : Убедиться, что Docker-демон запущен и включён] ***********************************************************************************************************************************************************************************************************************************************************************************
ok: [51.250.45.157]

TASK [wordpress : Дождаться восстановления SSH-соединения после установки Docker] ******************************************************************************************************************************************************************************************************************************************************************
ok: [51.250.45.157]

TASK [wordpress : Создать директорию для WordPress файлов] *****************************************************************************************************************************************************************************************************************************************************************************************
ok: [51.250.45.157]

TASK [wordpress : Скопировать шаблон docker-compose.yml в директорию] ******************************************************************************************************************************************************************************************************************************************************************************
ok: [51.250.45.157]

TASK [wordpress : Остановить и удалить старые контейнеры и тома] ***********************************************************************************************************************************************************************************************************************************************************************************
[WARNING]: Docker compose: unknown None: /home/ubuntu/wordpress/docker-compose.yml: the attribute `version` is obsolete, it will be ignored, please remove it to avoid potential confusion
ok: [51.250.45.157]

TASK [wordpress : Запустить контейнеры через Docker Compose с пересборкой] *************************************************************************************************************************************************************************************************************************************************************************
changed: [51.250.45.157]

TASK [wordpress : Дождаться завершения задачи запуска контейнеров Docker Compose] ******************************************************************************************************************************************************************************************************************************************************************
FAILED - RETRYING: [51.250.45.157]: Дождаться завершения задачи запуска контейнеров Docker Compose (30 retries left).
FAILED - RETRYING: [51.250.45.157]: Дождаться завершения задачи запуска контейнеров Docker Compose (29 retries left).
FAILED - RETRYING: [51.250.45.157]: Дождаться завершения задачи запуска контейнеров Docker Compose (28 retries left).
FAILED - RETRYING: [51.250.45.157]: Дождаться завершения задачи запуска контейнеров Docker Compose (27 retries left).
FAILED - RETRYING: [51.250.45.157]: Дождаться завершения задачи запуска контейнеров Docker Compose (26 retries left).
FAILED - RETRYING: [51.250.45.157]: Дождаться завершения задачи запуска контейнеров Docker Compose (25 retries left).
FAILED - RETRYING: [51.250.45.157]: Дождаться завершения задачи запуска контейнеров Docker Compose (24 retries left).
FAILED - RETRYING: [51.250.45.157]: Дождаться завершения задачи запуска контейнеров Docker Compose (23 retries left).
FAILED - RETRYING: [51.250.45.157]: Дождаться завершения задачи запуска контейнеров Docker Compose (22 retries left).
FAILED - RETRYING: [51.250.45.157]: Дождаться завершения задачи запуска контейнеров Docker Compose (21 retries left).
FAILED - RETRYING: [51.250.45.157]: Дождаться завершения задачи запуска контейнеров Docker Compose (20 retries left).
FAILED - RETRYING: [51.250.45.157]: Дождаться завершения задачи запуска контейнеров Docker Compose (19 retries left).
FAILED - RETRYING: [51.250.45.157]: Дождаться завершения задачи запуска контейнеров Docker Compose (18 retries left).
FAILED - RETRYING: [51.250.45.157]: Дождаться завершения задачи запуска контейнеров Docker Compose (17 retries left).
FAILED - RETRYING: [51.250.45.157]: Дождаться завершения задачи запуска контейнеров Docker Compose (16 retries left).
FAILED - RETRYING: [51.250.45.157]: Дождаться завершения задачи запуска контейнеров Docker Compose (15 retries left).
FAILED - RETRYING: [51.250.45.157]: Дождаться завершения задачи запуска контейнеров Docker Compose (14 retries left).
FAILED - RETRYING: [51.250.45.157]: Дождаться завершения задачи запуска контейнеров Docker Compose (13 retries left).
FAILED - RETRYING: [51.250.45.157]: Дождаться завершения задачи запуска контейнеров Docker Compose (12 retries left).
FAILED - RETRYING: [51.250.45.157]: Дождаться завершения задачи запуска контейнеров Docker Compose (11 retries left).
changed: [51.250.45.157]

PLAY RECAP *****************************************************************************************************************************************************************************************************************************************************************************************************************************************
51.250.45.157              : ok=14   changed=4    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
```

## Проверка работы с MASTER-MySQL
```bash
sudo docker exec -it wordpress-db_master-1 mysql --protocol=TCP -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 19
Server version: 8.0.40 Source distribution

Copyright (c) 2000, 2024, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> SHOW MASTER STATUS;
+------------------+----------+--------------+------------------+-------------------+
| File             | Position | Binlog_Do_DB | Binlog_Ignore_DB | Executed_Gtid_Set |
+------------------+----------+--------------+------------------+-------------------+
| mysql-bin.000003 |      157 |              |                  |                   |
+------------------+----------+--------------+------------------+-------------------+
1 row in set (0.00 sec)

mysql> CREATE DATABASE IF NOT EXISTS test_replication;
Query OK, 1 row affected (0.02 sec)

mysql> USE test_replication;
Database changed
mysql> CREATE TABLE test_table (id INT AUTO_INCREMENT PRIMARY KEY, msg VARCHAR(255));
Query OK, 0 rows affected (0.11 sec)

mysql> INSERT INTO test_table (msg) VALUES (' ');
Query OK, 1 row affected (0.03 sec)

mysql> exit
Bye
```

## Проверка работы с SLAVE-MySQL
```bash
sudo docker exec -it wordpress-db_slave-1 mysql --protocol=TCP -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 17
Server version: 8.0.40 Source distribution

Copyright (c) 2000, 2024, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> USE test_replication;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> SELECT * FROM test_table;
+----+------+
| id | msg  |
+----+------+
|  1 |      |
+----+------+
1 row in set (0.00 sec)

mysql> 
```
