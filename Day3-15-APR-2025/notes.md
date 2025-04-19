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




IQ] where the maven default home dir?

  cd ~/.m2/repository/

  ls -lrth ---> you will see the dependecies.


IQ] How to change the maven default dir?
ANS:
   step 1: cd ~ ---> goto home dir
   step 2: create one custom dir --->   mkdir mavenlocalrepo
   step 3:  /root/customMavenRepo/  -----> copy this path
   step 4: <localRepository>/root/customMavenRepo</localRepository>  ---> add this into /conf/settings.xml  

   step 5: cd /opt/apache-maven-3.9.8/conf/
   step 6: open the settings.xml
   step 7: add this <localRepository>/root/mavenlocalrepo/</localRepository>
  
NOTE: Now you can run the mvn clean package : It will again downloading from centrol repo.



IQ] Then what is the use of mvn clean install?
ANS: It will store a package in maven local repo ---> /root/mavenlocalrepo/com/   Here it  	will store.

  mvn clean install  ---> It will create package into maven local repo and target dir.


mvn clean deploy


b4devopshyd.pem


scp -i ~/Downloads/b4devopshyd.pem backend.zip ec2-user@18.61.75.128:/home/ec2-user/
