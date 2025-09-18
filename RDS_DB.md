Begin Configuration :

sudo su -
yum install mariadb105 -y
systemctl enable mariadb
systemctl start mariadb
yum -y update
