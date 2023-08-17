## login
```bash
# login to remote server
ssh -i "key.pem" ec2-user@ec2-54-152-125-86.compute-1.amazonaws.com

#===========================
# install nginx with yum
#===========================
# 1. change role to root
sudo su -

# 2. install nginx
yum install nginx -y

# 3. start nginx
systemctl start nginx

# 4. check status
systemctl status nginx

# 5. start nginx when booting
systemctl enable nginx

# 6. check amazon linux public ip ( 54.152.125.86 )
dig +short myip.opendns.com @resolver1.opendns.com
or
curl http://checkip.amazonaws.com

# install git
yum install git -y

# add a basic nginx config
# dir: /etc/nginx/conf.d
server {
    listen       80;
    listen       [::]:80;
    server_name  leling-tech.com www.leling-tech.com;
    root         /www/leling;
}
```