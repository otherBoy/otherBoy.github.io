---
layout: post
title: Starter of RabbitMQ
date: 2017-10-09 16:00:00.000000000 +09:00
tags: RabbitMQ
---

#### 1. Install RabbitMQ

Since MacOS has integrated Erlang internally, it is quite easy to install RabbitMQ server on MacOS.

```
brew update
brew install rabbitmq
```
#### 2. Add RabbitMQ path to bash profile
```
sudo vim ~/.bash_profile
```
add **export PATH=$PATH:/usr/local/sbin** at the end of the file, then save and quite.

```
source ~/.bash_profile
```

#### 3. Start RabbitMQ server
```
rabbitmq-server
```

#### 4. Add credentials
You can use the command below to check all existing users and their authority.

```
sudo rabbitmqctl list_users
```

>Listing users</br>
guest	[administrator]

Create a new user and set its authority and vhosts.

```
sudo rabbitmqctl add_user gekko 123456
sudo rabbitmqctl set_user_tags gekko administrator
```
>Setting tags for user "gekko" to [administrator]

```
sudo rabbitmqctl set_permissions -p / gekko ".*" ".*" ".*"
```
Add node info such as node name, ip address to RabbitMQ env file.
**CONFIG_FILE=/usr/local/etc/rabbitmq/rabbitmq**</br>
**NODE****_****IP****_****ADDRESS=127.0.0.1**</br>
**NODENAME=rabbit@localhost**

```
sudo vim /usr/local/etc/rabbitmq/rabbitmq-env.conf
```
Save the configuration and restart RabbitMQ server.


