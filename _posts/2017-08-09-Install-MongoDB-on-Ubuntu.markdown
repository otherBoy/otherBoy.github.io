---
layout: post
title: Install MongoDB on Ubuntu-16.04
date: 2017-08-19 17:20:00.000000000 +09:00
tags: MongoDB
---

#### 1. Download MongoDB package
MongoDB official download link: 
[https://www.mongodb.com/download-center?jmp=nav#community](https://www.mongodb.com/download-center?jmp=nav#community)

```
wget https://fastdl.mongodb.org/linux/mongodb-linux-x86_64-ubuntu1604-3.4.7.tgz
```

#### 2. Unzip MongoDB package
```
tar -zxvf mongodb-linux-x86_64-ubuntu1604-3.4.7.tgz
```

#### 3. Move MongoDB folder to local
```
sudo mv mongodb-linux-x86_64-ubuntu1604-3.4.7/ /usr/local/mongodb
```

#### 4. Create data directory
The default directory for data storage of MongoDB is ```/data/db```.<br>
Normally, we use the default directory.

```
sudo mkdir -p /data/db
sudo chown -R 'username' /data/db
```

#### 5. Test MongoDB
```
cd /usr/local/mongodb/bin/
./mongod
```
<br>
****
We can also use apt-get to install MongoDB on Ubuntu.

```
sudo apt install mongodb-server
```

MongoDB official tutorial for installation: [https://docs.mongodb.com/v3.4/tutorial/install-mongodb-on-ubuntu/](https://docs.mongodb.com/v3.4/tutorial/install-mongodb-on-ubuntu/)
