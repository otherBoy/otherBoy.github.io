---
layout: post
title: Install Neo4j on Ubuntu-16.04
date: 2017-10-20 15:50:00.000000000 +09:00
tags: Neo4j
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

#### 1. Download Neo4j package
Neo4j official download link:</br>
[https://neo4j.com/download-thanks/?edition=community&release=3.2.5&flavour=unix](https://neo4j.com/download-thanks/?edition=community&release=3.2.5&flavour=unix)

```
wget https://neo4j.com/artifact.php?name=neo4j-community-3.2.5-unix.tar.gz
```

#### 2. Unzip Neo4j package
```
tar -zxvf neo4j-community-3.2.5-unix.tar.gz
sudo mv neo4j-community-3.2.5/ /opt/neo4j
```

uncomment **dbms.connectors.default_listen_address=0.0.0.0** in neo4j.conf

#### 3. Start Neo4j
```
cd /opt/neo4j/bin/
./neo4j start
```

>WARNING: Max 1024 open files allowed, minimum of 40000 recommended. See the Neo4j manual.
Started neo4j (pid 12648). It is available at http://0.0.0.0:7474/</br>
There may be a short delay until the server is ready.
See /opt/neo4j/logs/neo4j.log for current status.