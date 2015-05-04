# sparkwordcountapp

This is an example Standalone Spark word count application, written in Java and Scala, to demonstrate How to get started with Spark and MapR 4.1. 

Here is the spark-submit command to run the java word count, passing the input file and output directory as  arguments to the main method of the JavaWordCount class:

/opt/mapr/spark/spark-1.2.1/bin/spark-submit --class example.wordcount.JavaWordCount --master yarn \
  sparkwordcount-1.0.jar /user/user01/input/alice.txt /user/user01/output

Here is the spark-submit command to run the scala word count, passing the input file and output directory as arguments to the SparkWordCount class:

/opt/mapr/spark/spark-1.2.1/bin/spark-submit --class SparkWordCount --master yarn \
  sparkwordcount-1.0.jar /user/user01/input/alice.txt /user/user01/output

