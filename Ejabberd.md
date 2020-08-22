# Set Host name 
```
hostnamectl set-hostname [YOUR DOMAIN]
vi /etc/hosts
127.0.0.1  [YOUR DOMAIN]
ls -l /etc/cloud/cloud.cfg
vi /etc/cloud/cloud.cfg
preserve_hostname: true
hostnamectl
```


# Install Apache2 
```
apt update 
apt install apache2
```
# Install certbot 
```
apt install software-properties-common
add-apt-repository universe
add-apt-repository ppa:certbot/certbot
apt update
apt-get install certbot python3-certbot-apache
```
# Generate certs 
```
certbot --apache -d [YOUR DOMAIN]
```
Copy paths of key and cert:
```
/etc/letsencrypt/live/[YOUR DOMAIN]/privkey.pem
/etc/letsencrypt/live/[YOUR DOMAIN]/fullchain.pem
```
We need to set them on ejabberd yml file. 

# Pre Requirements
To compile ejabberd on a ‘Unix-like’ operating system, you need:
```
apt install automake
apt install build-essential
apt install libexpat-dev
apt install libyaml-dev
apt install erlang
apt install libssl-dev
apt install zlib1g-dev
apt install libpam0g-dev
apt install imagemagick
```
# Clone and build Ejabberd code
```
git clone https://github.com/processone/ejabberd.git
cd ejabberd
./autogen.sh
./configure --enable-user=root --enable-mysql --enable-new-sql-schema --prefix=/opt/ejabberd_mysql
make
make install
```
# Check if its working 
```
/opt/ejabberd_mysql/sbin/ejabberdctl start
/opt/ejabberd_mysql/sbin/ejabberdctl status
```
# Stop Ejabberd 
```
/opt/ejabberd_mysql/sbin/ejabberdctl stop
```
