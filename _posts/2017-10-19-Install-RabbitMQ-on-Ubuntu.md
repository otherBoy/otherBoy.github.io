---
layout: post
title: Install RabbitMQ Server on Ubuntu-16.04
date: 2017-18-19 09:20:00.000000000 +09:00
tags: RabbitMQ
---

#### 1. Install Erlang
Erlang is required to run RabbitMQ server. Therefore, we need to install Erlang first.

```
sudo apt-get update
sudo apt-get upgrade
```

```
cd /tmp
wget http://packages.erlang-solutions.com/ubuntu/erlang_solutions.asc
sudo apt-key add erlang_solutions.asc
sudo apt-get update
sudo apt-get install erlang
sudo apt-get install erlang-nox
```

#### 2. Add RabbitMQ repository

```
sudo vim /etc/apt/sources.list
```
Add "**deb http://www.rabbitmq.com/debian/ testing main**" at the end of the file, then save and quit.

#### 3. Add secret key

```
cd /tmp
wget https://www.rabbitmq.com/rabbitmq-signing-key-public.asc
sudo apt-key add rabbitmq-signing-key-public.asc
sudo apt-get update
``` 

#### 4. Install RabbitMQ server

```
sudo apt-get install rabbitmq-server
```

#### 5. Start RabbitMQ server

```
sudo systemctl enable rabbitmq-server
sudo systemctl start rabbitmq-server
```

#### 6. Enable RabbitMQ management plugin

```
sudo rabbitmq-plugins enable rabbitmq_management
```

After enable plugins, we have to restart RabbitMQ server.

```
sudo systemctl restart rabbitmq-server
```

#### 7. Check the status of RabbitMQ server

```
sudo systemctl status rabbitmq-server
```

#### 8. Manage RabbitMQ server through web
If everything goes well, we can visit the RabbitMQ server through [http://xx.xx.xx.xx:15672](http://xx.xx.xx.xx:15672), xx.xx.xx.xx is your server's ip address.</br>
The default username and password to login is guest/guest.

