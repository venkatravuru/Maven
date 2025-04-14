sample pom.xml   [Project Object Model]
--------------
<project>
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.jio</groupId>
    <artifactId>jio-project</artifactId>
    <version>1.0.0</version>
    <packaging>war</packaging>

    <name>Sample Project</name>
    <url>http://www.example.com</url>

    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- JUnit for unit testing -->
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
            <scope>test</scope>
        </dependency>
      <!-- https://mvnrepository.com/artifact/log4j/log4j  -->
	<dependency>
    	<groupId>log4j</groupId>
    	<artifactId>log4j</artifactId>
    	<version>1.2.17</version>
	</dependency>


    </dependencies>


    <profiles>
        <profile>
            <id>dev</id>
            <properties>
                <environment>development</environment>
            </properties>
        </profile>
        <profile>
            <id>prod</id>
            <properties>
                <environment>production</environment>
            </properties>
        </profile>
    </profiles>

</project>










Testing frameworks
-------------------
java ---> Junit 
java script ---> Jest
Python ---> pytest
c#  ---> NUnit
Ruby ---> RSpec
c++  ---> gtest
Go  ----> Testfy

what is test case here?
-----------------------
To test the source code programmatically, we are using test cases, These are developed by developers not a DevOps Engineers

EX: to run the Junit test cases we required below dependency

          <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
            <scope>test</scope>
         </dependency>



IQ) From where these dependencies are downloaded while running?

ANS
---

central repo



Maven repositories 
==================


Maven repositories are locations where Maven artifacts (JAR files, plugins, and other project dependencies) are stored and can be retrieved from.


1. maven local repository
--------------------------
--> The local repository is a directory on your local machine where Maven stores downloaded artifacts. By default, it is located in the .m2 directory within the user's home directory.


linux: ~/.m2/repository
windows: C:\Users\prasanth\.m2\repository
mac book: /users/prasanth/.m2/repository

IQ] Is it possible to change the default location?
ANS: Yes

step 1:
-----
open /conf/settings.xml

step 2:
----

<localRepository>
/root/commonmavenrepo/     
</localRepository>


IQ] why we need to change ?
ANS: For every user we have separate local repo then Hard disk space is increased , so we are giving common repo to all dev team.


2. maven central repository
----------------------------
The central repository is the default repository used by Maven, hosted by the Maven community. It contains a vast number of commonly used libraries. If a dependency is not found in the local repository, Maven searches the central repository.

URL: https://repo.maven.apache.org/maven2/






3. maven remote repository
--------------------------

EX: Nexus / JFrog

In your orgnaization, We have 5 war files,every one c Dont keep in the cenral repo, why?, an access, so we are keeping in remote repo so our company people can access.

NOTE: we will discuss in nexus classes.


Maven life cycles
=================


1. clean Lifecycle
-------------------
goals
-----
The clean lifecycle handles project cleaning. It consists of the following phases:

pre-clean: 
clean: It will delete the build history --> delete the target dir.
post-clean:


EX: mvn clean


2. Site Lifecycle
-----------------
golas
-----
The site lifecycle handles the creation of the project's site documentation. It consists of the following phases:

pre-site: Executes processes needed before the actual project site generation.
site:     Generates the project's site documentation.
post-site:    Executes processes needed to finalize the site generation.
site-deploy: Deploys the generated site documentation to the specified web server.



mvn site


NOTE: Now a days developers are using Swagger instead of site goal.



3. default Lifecycle (most commonly used)
------------------------------------------

validate - validate the project is correct and all necessary information is available like directory structure, etc

mvn validate

compile - compile the source code of the project

mvn comiple



test - test the compiled source code using a suitable unit testing framework[junit] and     	checks the unit test cases.
        NOTE:   These tests should not require the code be packaged or deployed



mvn test

package - take the compiled code and and generate the package, such as a jar/war/ear.

mvn package  



install - install the package[jar/war/ear] into the local repository, for use as a 	dependency in other projects locally.

mvn install 



deploy - done in the build environment, copies the final package[jar/war/ear] to the 	remote repository for sharing with other developers and projects.

mvn deploy 

Examples:
mvn clean
mvn validate
mvn compile
mvn test
mvn package
mvn verify
mvn install
mvn deploy


Is it possible to pass two goals at a time?


mvn clean package





IQ] diff b/w install and deploy?
ANS:

IQ] can we use more than one goal name along with mvn command?
ANS: Yes
EX:  mvn clean package [first it will execute clean and then package]

IQ] How to skip the unit test cases?

EX: mvn clean package -DskipTests
    mvn clean package -Dmaven.test.skip=true




==============================================================================

LAB
----

step 1: clone the code from github

    git clone <url>

step 2: go to that directory

step 3: see the data inside : tree ----> source code and unit test cases.

step 4: mvn clean package [It will download all dependecies from central repo at first time]

step 5: mvn clean package [ check where again downloading or not]

step 6: ls target/
     classes ---> .class files
     test-classes ---> unit test .class files

NOTE : pls run the maven commands where the pom.xml file is available.

step 7: mvn clean ---> It will delete the target directory.



How to skip running unit test cases?
ANS:
   mvn clean package -DskipTests  ---> It will skip only unit test cases but compilation will done

   mvn clean package -Dmaven.test.skip=true ---> It will skip unit test cases and comilation also 
