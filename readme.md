# Install Mail Server (squirrelmail)

install beberapa dependencies
```
apt -y install ca-certificates software-properties-common python3-software-properties
```

```
locale-gen id_ID.UTF-8
```

```
apt -y install apache2 php php-xmlrpc php-mysql php-gd php-cli \
php-curl dovecot-common dovecot-imapd \
dovecot-pop3d postfix php-mbstring \
php-xdebug libapache2-mod-php unzip
```

```
internet with smarthost
sebastian.com
smtp.telkom.net
```

```
cd /usr/local/src
git clone https://github.com/RealityRipple/squirrelmail
mv squirrelmail /var/www/html/squirrelmail/
mkdir -p /var/local/squirrelmail/data
chown -Rf www-data: /var/local/squirrelmail/
chmod -Rf 777 /var/local/squirrelmail/
```

```
cd /var/www/html/squirrelmail/
```

```
./configure
```

2 -> 1 -> sebastian.com -> s -> q

```
service dovecot restart
/etc/init.d/apache2 restart
/etc/init.d/postfix restart
```

menambahkan email

```
useradd anggi
useradd daniel
useradd geyl
useradd meily
useradd sebastian
```

```
passwd anggi
```

```
passwd daniel
```

```
passwd geyl
```

```
passwd meily
```

```
passwd sebastian
```

```
mkdir -p /var/www/html/anggi
mkdir -p /var/www/html/daniel
mkdir -p /var/www/html/geyl
mkdir -p /var/www/html/meily
mkdir -p /var/www/html/sebastian
usermod -m -d /var/www/html/anggi anggi
usermod -m -d /var/www/html/daniel daniel
usermod -m -d /var/www/html/geyl geyl
usermod -m -d /var/www/html/meily meily
usermod -m -d /var/www/html/sebastian sebastian
```

```
chown -R anggi:anggi /var/www/html/anggi
chown -R daniel:daniel /var/www/html/daniel
chown -R geyl:geyl /var/www/html/geyl
chown -R meily:meily /var/www/html/meily
chown -R sebastian:sebastian /var/www/html/sebastian
```

emailnya
anggi@sebastian.com;
daniel@sebastian.com;
geyl@sebastian.com;
meily@sebastian.com;
sebastian@sebastian.com;


# Install LAMP (Linux Apache Mysql PHP)
### Install Apache    

allow apache
```
ufw allow in "Apache"
ufw allow in "Apache Full"
```

### Install MYSQL
```
apt install mysql-server
```
```
systemctl start mysql
```
```
mysql_secure_installation
```
```
y -> 0 -> y -> y -> y -> y -> y
```

### Setting MYSQL
```
mysql
```

```
create user 'server'@'localhost' identified by 'server123';
```

```
grant all privileges on *.* to 'server'@'localhost';
```

```
flush privileges;
```

```
exit
```

```
mysql -u server -p
```
password : server123


coba buat database, tablenya dan isinya
```
create database db_mahasiswa;
use db_mahasiswa;
create table mahasiswa(
id int primary key auto_increment,
nama varchar(100),
nim varchar(9),
email varchar(100)
);
insert into mahasiswa (nama, nim, email) values
('Anggi Yohanes Pardede', '191402143', 'anggiyohanespdd@gmail.com'),
('Daniel Situmeang', '191402140', 'dsitumeang47@gmail.com'),
('Geylfedra Matthew Panggabean', '191402065', 'geylrillas@gmail.com'),
('Meily Benedicta', '191402053', 'meilybenedicta2001@gmail.com'),
('Sebastian Belmero Sitorus', '191402113', 'sebastian.belmero.1@gmail.com');
exit;
```