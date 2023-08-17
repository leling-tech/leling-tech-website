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
# nginx dir: /etc/nginx/conf.d
# repo dir: /www/leling
server {
    listen       80;
    listen       [::]:80;
    server_name  leling-tech.com www.leling-tech.com;
    root         /www/leling;
}

#=======================
# install certbot
#=======================
# choose nginx and fedora for amazon linux 2023
# https://certbot.eff.org/instructions?ws=nginx&os=fedora

# remove old dependencies
dnf remove certbot

# install python3 with python/pip
dnf install python3 augeas-libs

# install pip
python3 -m venv /opt/certbot/ && sudo /opt/certbot/bin/pip install --upgrade pip

# install with pip
/opt/certbot/bin/pip install certbot certbot-nginx

# symbollink
ln -s /opt/certbot/bin/certbot /usr/bin/certbot

# configure nginx
certbot --nginx
```