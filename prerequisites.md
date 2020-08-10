# Initial Server Setup with Ubuntu

## Introduction
There are a few configuration steps that you should take early on as part of the basic setup. This will increase the security and usability of your server and will give you a solid foundation for subsequent actions.

## Step 1 -- Logging in as Root
## Step 2 -- Creating a New User
```
# adduser melon
```
Enter a strong password and, optionally, fill in any of the additional information if you would like.

## Step 3 -- Granting Administrative Privileges
```
# usermod -aG sudo melon
```
As root, run this command to add your new user to the sudo group.  

Users who belong to the sudo group are allowed to use the sudo command by putting the word 'sudo' before each command.

命令usermod的options：  
    1. -a, --append
    2. -d, --home
    3. -G, --groups
    4. -p, --password
    
 ## Step 4 -- Setting up a Basic Firewall
```
ufw app list
```
查看在防火墙内注册过的应用  

Different applications can register their profiles with UFW upon installation.  

可以选择启动防火墙，这样会拦截所有不被允许的请求
