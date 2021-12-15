# Moodle-Build

# 更新Rockey-Linux
sudo yum -y update;
sudo yum -y install vim;
sudo yum -y install tmux;
sudo yum -y install zip;
sudo yum -y install unzip;
sudo yum -y install git;
sudo yum -y install wget;
# 安裝 Apache
1.下載 Apache
sudo yum -y install httpd;
2.啟用 Apache
sudo systemctl enable httpd;
sudo systemctl start httpd;
# 安裝 PHP 7.3
1.下載 PHP7.3 資源包
sudo dnf install dnf-utils http://rpms.remirepo.net/enterprise/remi-release-8.rpm -y
2.啟用 PHP7.3
sudo dnf module reset php -y;
sudo dnf module enable php:remi-7.3 -y;
3.安裝 PHP7.3
sudo dnf install php -y;
sudo dnf install php-gd php-mysqlnd php-soap php-zip php-intl php-xmlrpc php-sodium -y;
# 安裝 Mariadb
1.下載 Mariab-Server
sudo yum install mariadb-server -y;
2.啟用 Mariadb
sudo systemctl enable mariadb;
sudo systemctl start mariadb;
3.設定 Mariadb 資料庫字元
set character_set_server = 'latin1';
set character_set_results = 'utf8';
set character_set_filesystem = 'binary';
set character_set_database = 'latin1';
set character_set_connection = 'utf8';
set character_set_client = 'utf8';
4.創建 Mariadb 資料庫
create database moodle;
5.添加 Mariadb 使用者
CREATE USER 'ksu'@'%' IDENTIFIED BY 'PASSWORD';
GRANT ALL PRIVILEGES ON . TO 'ksu'@'%' IDENTIFIED BY 'PASSWORD';
FLUSH PRIVILEGES;
exit;



# 安裝 Moodle
1.進入 Apache 網頁位置
cd /var/www/html
2.下載 Moodle 
sudo git clone https://github.com/moodle/moodle.git
or
sudo wget https://download.moodle.org/stable311/moodle-latest-311.zip

sudo chown -R apache /var/www/html
# 關閉SELINUX防火牆
sestatus
sudo vim /etc/selinux/config
SELINUX=disabled
# 開啟 80 Port
sudo firewall-cmd --add-service=http --permanent
sudo firewall-cmd --reload
sudo firewall-cmd --list-all
sudo reboot

sudo mysql -u root -p

