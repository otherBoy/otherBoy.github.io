---
layout: post
title: Elasticsearch-5.x Configuration
date: 2017-08-10 09:00:01.000000000 +09:00
tags: Elasticsearch
---

#### 1. Install Java
Elasticsearch is built using **Lucene Core** which is a Java-based indexing and search technology. In order to run Elasticseach, we have to **install Java first**.<br>

Add repository for JDK

```
sudo add-apt-repository ppa:webupd8team/java
```
Update Ubuntu software package repository

```
sudo apt-get update
```
Install JDK 8

```
sudo apt-get install oracle-java8-installer
```
Verify that Java is installed

```
java -version
javac -version
```
If you see info as below, Java is installed successfully.
> java version "1.8.0_144"
> 
> Java(TM) SE Runtime Environment (build 1.8.0_144-b01)
> 
> Java HotSpot(TM) 64-Bit Server VM (build 25.144-b01, mixed mode)
> 
> javac 1.8.0_144

Set up environment

```
sudo vim /etc/profile
```
Add these lines of code at the end of the file

```
export JAVA_HOME=/usr/lib/jvm/java-8-oracle
export JRE_HOME=$JAVA_HOME/jre
export CLASSPATH=$CLASSPATH:$JAVA_HOME/lib:$JAVA_HOME/jre/lib
export PATH=$PATH:$JAVA_HOME/bin:$JAVA_HOME/jre/bin
```
Enforcing the changes we have made to the current environment

```
source /etc/profile
```

#### 2. Download Elasticsearch package
Elasticsearch official download link: [https://www.elastic.co/downloads/elasticsearch](https://www.elastic.co/downloads/elasticsearch)

```
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-5.4.3.tar.gz
```

#### 3. Unzip Elasticsearch package
```
tar -zxvf elasticsearch-5.4.3.tar.gz
sudo mv elasticsearch-5.4.3/ /opt/elasticsearch
```

#### 4. Run Elasticsearch
```
cd /opt/elasticsearch/bin/
./elasticsearch
```
##### If you get the error below, try to modify elasticsearch directory owner to fix it.
> 587 main ERROR Could not register mbeans java.security.AccessControlException: access denied ("javax.management.MBeanTrustPermission" "register")

```
sudo chown -R 'username' /opt/elasticsearch/
```
##### You may also encounter the error below.
> bootstrap checks failed </br>
> max virtual memory areas vm.max_map_count [65530] is too low, increase to at least [262144]

```
sudo sysctl -w vm.max_map_count=262144
```

#### 5. Download Kibana package
Kibana official download link: [https://www.elastic.co/downloads/kibana](https://www.elastic.co/downloads/kibana)

```
wget https://artifacts.elastic.co/downloads/kibana/kibana-5.4.3-linux-x86_64.tar.gz
```

#### 6. Unzip Kibana package
```
tar -zxvf kibana-5.4.3.tar.gz
sudo mv kibana-5.4.3/ /opt/kibana
```

#### 7. Run Kibana
```
cd /opt/kibana/bin/
./kibana
```

---
By default, Elasticsearch and Kibana only allow **localhost**. If you want to operate remotely, you need to modify **config/elasticsearch.yml** and **config/kibana.yml**. Uncomment **network.host** and modify **localhost** to **0.0.0.0**, and then reboot Elasticsearch and Kibana.

```
network.host: 0.0.0.0
```
