# sparkwordcountapp

This is an example Standalone Spark word count application, written in Java and Scala, to demonstrate How to get 
started with Spark and MapR. 


Install and fire up the Sandbox using the instructions here: http://maprdocs.mapr.com/home/SandboxHadoop/c_sandbox_overview.html. 

Next, use an SSH client such as Putty (Windows) or Terminal (Mac) to login. See below for an example:
use userid: user01 and password: mapr.

For VMWare use:  $ ssh user01@ipaddress 

For Virtualbox use:  $ ssh user01@127.0.0.1 -p 2222 

Spark can be linked into applications in either Java, Scala, or Python. 
Maven is a popular package management tool for Java-based languages that lets you link to libraries in public repositories. In Java and Scala, you give your application a Maven dependency on the spark-core artifact. The current Spark version is 1.6.1 and the Maven coordinates are:

    <repositories>
        <repository>
            <id>scala-tools.org</id>
            <name>Scala-tools Maven2 Repository</name>
            <url>http://scala-tools.org/repo-releases</url>
        </repository>
        <repository>
            <id>mapr-releases</id>
            <url>http://repository.mapr.com/maven/</url>
            <snapshots>
                <enabled>false</enabled>
            </snapshots>
            <releases>
                <enabled>true</enabled>
            </releases>
        </repository>
    </repositories>

        <dependency>
            <groupId>org.apache.spark</groupId>
            <artifactId>spark-core_2.10</artifactId>
            <version>1.6.1</version>
            <scope>provided</scope>
        </dependency>


You can build with Maven using IDEs like Eclipse or NetBeans, and then copy the JAR file to your MapR Sandbox, or you can install Maven on your sandbox and build from the Linux command line.

You can use scp to copy your JAR file to the MapR Sandbox:

See below for an example of using scp from the command line:
use userid: user01 and password: mapr.
For VMWare use:  $ scp  nameoffile.jar  user01@ipaddress:/user/user01/. 

For Virtualbox use:  $ scp -P 2222 nameoffile.jar  user01@127.0.0.1:/user/user01/.  

Running Your Application

First find the version of Spark on the sandbox with  ls /opt/mapr/spark/  Then you can use the spark commands in the /opt/mapr/spark/spark-version/bin directory.
You use the bin/spark-submit script to launch your application. This script takes care of setting up the classpath with Spark and its dependencies. Here is the spark-submit format:

/opt/mapr/spark/spark-<version>/bin/spark-submit \
  --class <main-class>
  --master <master-url> \
  <application-jar> \
  [application-arguments]


Here is the spark-submit command to run the java word count, passing the input file and output directory as  arguments to the main method of the JavaWordCount class:

/opt/mapr/spark/spark-1.6.1/bin/spark-submit --class example.wordcount.JavaWordCount --master yarn \
  sparkwordcount-1.0.jar /user/user01/input/alice.txt /user/user01/output

Here is the spark-submit command to run the scala word count, passing the input file and output directory as arguments to the SparkWordCount class:

/opt/mapr/spark/spark-1.6.1/bin/spark-submit --class SparkWordCount --master yarn \
  sparkwordcount-1.0.jar /user/user01/input/alice.txt /user/user01/output

