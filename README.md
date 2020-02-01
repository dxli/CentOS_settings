# CentOS Enviroment Setup
Setting CentOS up for Django
## Repositories needed
Enable repositories: AppStream, epel-playground
```console
[foo@bar:~]# dnf config-manager --set-enabled AppStream epel-playground
```
## Install SQL packages
### install mariadb-server
```console
[foo@bar:~]# dnf install mariadb-server
```
### start the mysql server and set a root password
```console
[foo@bar:~]# systemctl restart mariadb
[foo@bar:~]# mysql_secure_installation
```
To set a root password for MariaDB, if there's no password yet
```console
[foo@bar:~]# systemctl restart mariadb
[foo@bar:~]# mysqladmin -u root password "NEWPASSWORD"
```

### Create database 'renodb'
```console
[foo@bar:~]# mysql -u root -p root
MariaDB [(none)]> create database renodb;
MariaDB [(none)]> exit;
```

## Install django
```console
[foo@bar:~]# dnf install python3-django -y
```

### install connector
```console
[foo@bar:~]# dnf install mariadb-connector-c-devel
```
### install mysqlclient
```console
[foo@bar:~]# pip3 install mysqlclient
```

## Install pycharm
### install snapd
```console
[foo@bar:~]# dnf install snapd
```
```console
[foo@bar:~]# systemctl enable --now snapd.socket
[foo@bar:~]# ln -s /var/lib/snapd/snap /snap
```
### install pycharm-CE
```console
[foo@bar:~]# snap install pycharm-community --classic
```

