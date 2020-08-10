# Use-Nginx-in-Ubuntu

## Prerequisites
create a regular，non-root user with sudo privileges configured on your server
[Initial Server Setup with Ubuntu](./prerequisites.md)

## Step 1 -- Installing Nginx
Nginx is available in Ubuntu's default repositories.  
所以可以使用 apt packaging system 下载Nginx

```
sudo apt update
sudo apt install nginx
```
apt will install the most recent Nginx and any required dependencies to your server.

## Step 2 -- Adjusting the FireWall
```
sudo ufw app list
```
You get a list of the application profiles:
* Nginx Full: open both port 80 and port 443
* Nginx HTTP：open only port 80
* Nginx HTTPS： open only port 443

可以根据需要调整防火墙设置

## Step 3 -- Checking your Web Server
```
systemctl status nginx
```

## Step 4 -- Managing the Nginx Process
```
sudo systemctl stop nginx

sudo systemctl start nginx

sudo systemctl restart nginx

sudo systemctl reload nginx // 更新配置，无需中断nginx服务

sudo systemctl disable nginx // 开机自启动配置
sudo systemctl enable nginx
```

## Step 5 -- Setting Up Server Blocks
server block(相当于虚拟主机)

nginx has one server block enabled by default. 指向的资源路径是/var/www/html

配置自己的server block：
1. 新建资源目录
2. 在/etc/nginx/sites-available中创建配置文件
3. 创建链接到/etc/nginx/sites-enabled
4. 重启nginx

nginx 的服务配置目录：
    * /etc/nginx  所有nginx配置都存放在这
    * /etc/nginx/nginx.conf  nginx的全局配置文件
    * /etc/nginx/sites-available  存储可用服务的配置文件（每一个server block对应一个配置文件）
    * /etc/nginx/sites-enabled   nginx启动时会读取该目录中的配置文件以启动server block（配置文件为软链接，指向available目录下的配置文件）

Server Logs:
    * /var/log/nginx/access.log
    * /var/log/nginx/error.log