
# Setup Instructions for VM with MySQL on Vultr

## Login as root to the Ubuntu server on your Vultr console


### 1. Install MySQL

- Install 
```
apt-get install mysql-server
```
![Install MySQL](./images/fr0305-01_Ubuntu-install-mysql.png#img2 "Install MySQL")

- Check
```
mysql --version
```
![Check MySQL](./images/fr0305-02_Ubuntu-check-mysql.png#img2 "Check MySQL")

### 2. Secure MySQL

- Lock down MySQL - Running this script will ask you

```
mysql_secure_installation
```
      - Add password validation policy: Yes
      - Enter a "password validation policy level": 2
      - Enter a password for the user, root, to login to MySQL: xxxxxx
      - Remove anonymous users? Yes
      - Disallow root login remotely? No (Yes on a production server)
      - Remove test database and access to it? No 
      - Reload privilege tables now? Yes


![Secure MySQL](./images/fr0305-03_Ubuntu-secure-mysql.png#img2 "Secure MySQL")

- Stop, Start and check status of MySQL
```
systemctl stop mysql
systemctl start mysql
systemctl status mysql.service
```

![Mysql-setup-check-status](./images/et0303-05_Mysql-setup-check-status.png#img1 "Mysql-setup-check-status")


- Check MySql version.
```
mysqladmin -p -u root version
```

![Mysql-setup-check-version](./images/et0303-06_Mysql-setup-check-version.png#img1 "Mysql-setup-check-version")


 - Allow remote access to MySQL
```
nano /etc/mysql/mysql.conf.d/mysqld.cnf

Change line:         bind-address            = 127.0.0.1
to:                  bind-address            = 0.0.0.0
```
![Mysql-setup-nano-bind-address](./images/et0303-07_Mysql-setup-nano-bind-address.png#img1 "Mysql-setup-nano-bind-address")

```
systemctl restart mysql.service
netstat -tulnp | grep mysql
```

![Mysql-setup-allow-remote-access](./images/et0303-08_Mysql-setup-allow-remote-access.png#img1 "Mysql-setup-allow-remote-access")

- Open firewall rule for port 3306
```
ufw allow 3306/tcp
```
![Mysql-setup-open-firewall-port-3360](./images/et0303-09_Mysql-setup-open-firewall-port-3360.png#img1 "Mysql-setup-open-firewall-port-3360")

 
- Create and Grant Privileges to user account: nimdas with host %
    - Note: root@localhost has all rights and nimdas@% has all rights

   ```
   mysql -p
      password: xxxxxxxxxx

   mysql> CREATE USER 'nimdas'@'%' IDENTIFIED WITH mysql_native_password BY 'xxxxxxxxxxxx';
   mysql> GRANT ALL PRIVILEGES ON *.* TO 'nimdas'@'%';
   mysql> SELECT user,authentication_string,plugin,host FROM mysql.user;

   ```
![Mysql-setup-create-admin](./images/et0303-11_Mysql-setup-create-admin.png#img1 "Mysql-setup-create-admin")

 8. Stop and Start mysql From the VM console:
 ```
 systemctl stop mysql
 systemctl start mysql
 ```

 9. Login as nimdas remotely from your local PC with MySQL Shell. Don't save the password

```
mysqlsh \connect nimdas@xxx.xxx.xxx.xxx:3306

mysqlsh \sql SELECT user,authentication_string,plugin,host FROM mysql.user;
```
![Mysql-setup-login-admin-mysqlsh-local](./images/et0303-12_Mysql-setup-login-admin-mysqlsh-local.png#img1 "Mysql-setup-login-admin-mysqlsh-local")

 10. From VM console check disk usage and that MySQL is running

```
df

ps -aux | awk /mysqld/
```

![Mysql-setup-VM-console-df-ps](./images/et0303-13_Mysql-setup-VM-console-df-ps.png#img1 "Mysql-setup-VM-console-df-ps")
 
### Next Step - Create Website with SSL on your server: 

## [Create Website with SSL](../setup/fr0306_Setup-Website-SSL-Ubuntu.md)
