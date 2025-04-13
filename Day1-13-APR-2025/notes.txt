Linux
git and github
shell scripting/python


maven Build tool
-----------------
Why you need to use?
--------------------

--> explain (developer--->github--->maven--->tomcat)

Build: Build is a process of automating the packages(jar, war, ear)

--> Maven is a popular build automation and project management tool used primarily for Java projects.
--> Developed by the Apache Software Foundation.
--> Maven is an open source build tool.
--> Maven is a platform independent.
--> Maven is not an executable software(.exe), It is in the zip/tar.gz (download and extract)
--> if you want to download maven use this link below
   https://maven.apache.org/download.cgi  --> download maven zip file





What are the build tools?
-------------------------
java
----
Ant
maven
gradle

python
------
pybuilder

.net
----
MS Build
Nant

Ruby
----
Rake

go
--
go build tool


what is jar, war, ear ?
-----------------------

1. standalone applications [Jar]
------------------------
--> Java code
--> Jar contains (.class files)

2. web applications [war]
-------------------
--> JAVA code + web content (HTML/CSS3/JS/images)
--> war contains( jar+ HTML/CSS3/JS/Images)


3. enterprise applications[ear]
--------------------------
--> JAVA code + web content (HTML/CSS3/JS)+ standalone and web modules
--> ear contains( jar+war+HTML/CSS3/JS/Images+modules)

--> if you want to download maven use this link below
   https://maven.apache.org/download.cgi




Maven directory structure
--------------------------
bin ---> contains binary files [mvn, etc]

boot ---> contains jar files used at runtime 

conf ---> configuration files[settings.xml]

lib ---> contains library files[jars]

default xml file names for build scripts
=========================================

pom.xml ----> maven
build.xml --->ant
build.gradle[we can not use xml for gradle]  --->gradle


sudo yum install java -y  java 11 or 8 
sudo yum install maven -y   ---> maven 3.9.1





maven installation
===================
System Requirements 
--------------------
--> Maven 3.9+ requires JDK 8 or above to execute.
--> No memory minimum requirement
--> Disk [Approximately 10MB is required for the Maven installation itself.]
--> Operating System [No minimum requirement. Start up scripts are included as shell scripts (tested on many Unix flavors) and Windows batch files.]

NOTE: All the external software are stored in /opt directory


step 1: sudo su -  [switch to root user]
------



step 2: Install java
------
sudo su -

javac -version
#Login as a root user

NOTE: If you want to search in Linux server use below command

sudo yum search java | grep OpenJDK

java -version 
#Install JDK 1.8 
sudo yum install java-1.8.0-openjdk-devel -y

java 11
-------
sudo yum install java-11-openjdk-devel -y




step 3: Install maven 
------

Pre Requisite Software
-----------------------------
Java (JDK) is the Pre - Requisite Software for Maven.

javac -version

1) Login as a root user and change the directory to /opt/

sudo su -
cd /opt/

yum install wget unzip -y

2) Download the Maven Software

wget https://dlcdn.apache.org/maven/maven-3/3.9.9/binaries/apache-maven-3.9.9-bin.zip


unzip apache-maven-3.9.9-bin.zip


3) Set the class path/Environmental Variable

# User specific environment and startup programs


vi ~/.bash_profile  ---> add below two statements

export M2_HOME=/opt/apache-maven-3.9.9
export PATH=$PATH:$M2_HOME/bin

mvn -version or mvn -v ----> Not installed , you need to load 

source ~/.bash_profile
