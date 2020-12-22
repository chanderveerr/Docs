#   Install Coturn
```
apt update
apt install coturn
```
#  Enable Coturn
```
vi /etc/default/coturn

TURNSERVER_ENABLED=1
```
# Configure 
```
vi /etc/turnserver.conf

changes in configuration file are below:-


listening-port=3478                 % Default: 3478  
listening-ip=0.0.0.0    
external-public-ip/private-ip       % AWS EC2
min-port=10000
max-port=20000
Verbose
fingerprint
lt-cred-mech                        % long term connection
user=username:password              % format should be same
realm=DNSname                       % domain name(xyz.com)
log-file=/var/tmp/turn.log          % enabling logs 
```
### If connection broken or system hanged
```
reconnect server
cd /etc/
ls -a
rm -f .turnserver.conf.swo
rm -f .turnserver.conf.swp
```
# Coturn server control
```
systemctl stop coturn 
systemctl start coturn
systemctl status coturn
systemctl restart coturn
```
# Check logs
```
cat /var/tmp/turn.log
```





