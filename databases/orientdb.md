## OrientDB

 - [Resources](#resources)
 - [Install from source](#install-from-source)

### Resources

 - [Wiki docs](https://github.com/nuvolabase/orientdb/wiki)
 - [Binary protocol](https://github.com/nuvolabase/orientdb/wiki/Network-Binary-Protocol)

### Install from source

**Prerequisites:**

 - JDK with correct env path
 - [ant](http://ant.apache.org/bindownload.cgi)
 - [maven](http://maven.apache.org/download.cgi)

**Windows env paths:**

```
JAVA_HOME C:\Program Files\Java\jdk1.7.0_21
ANT_HOME D:\_Temp\apache-ant-1.9.0
PATH C:\Program Files\Java\jdk1.7.0_21\bin;%ANT_HOME%\bin;C:\maven-3.0.5\bin
```

**Building:**

```
git clone https://github.com/nuvolabase/orientdb.git // or git pull origin master
cd orientdb
mvn clean installg
```

Server will be located under ../releases/orientdb-graphed-1.4.0-SNAPSHOT. Blueprints can also be cloned separately and blueprints-core with blueprints-orient-graph copied over to the lib folder.
