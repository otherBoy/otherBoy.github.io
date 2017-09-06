---
layout: post
title: Elasticsearch-5.x Configuration
date: 2017-08-10 09:00:01.000000000 +09:00
tags: Elasticsearch
---

#### 1. Install Java
Elasticsearch is built using Lucene Core which is a Java-based indexing and search technology. In order to run Elasticseach, we have to install Java first.<br>

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