
# Commands_DB
Commands to deploy DB in EC2

STEP 1 : Begin Configuration

```bash
sudo su -
yum install mariadb105 -y
systemctl enable mariadb
systemctl start mariadb
yum -y update  

STEP 2 : Set Environmental Variables
```bash
DBName=ec2db
DBPassword=admin123456
DBRootPassword=admin123456
DBUser=ec2dbuser

STEP 3 : Database Setup on EC2 Instance:

echo "CREATE DATABASE ${DBName};" >> /tmp/db.setup
echo "CREATE USER '${DBUser}' IDENTIFIED BY '${DBPassword}';" >> /tmp/db.setup
echo "GRANT ALL PRIVILEGES ON *.* TO '${DBUser}'@'%';" >> /tmp/db.setup
echo "FLUSH PRIVILEGES;" >> /tmp/db.setup
mysqladmin -u root password "${DBRootPassword}"
mysql -u root --password="${DBRootPassword}" < /tmp/db.setup
rm /tmp/db.setup

