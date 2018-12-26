## job history
https://blog.csdn.net/stark_summer/article/details/46459701
1. spark-defaults.conf 增加如下内容
```
spark.eventLog.enabled true 
spark.eventLog.dir hdfs://master.com:8020/var/log/spark 
spark.eventLog.compress true
```
2. spark-env.sh 增加如下内容
```
export SPARK_HISTORY_OPTS="-Dspark.history.ui.port=18080 -Dspark.history.retainedApplications=3 -Dspark.history.fs.logDirectory=hdfs:/master.com:8020/var/log/spark"
```

3. 启动start-history-server.sh
SPARK_HOME/conf 下: 执行 
```
./start-history-server.sh
```

4. spark job history web: master:18080

## running mode
https://www.jianshu.com/p/65a3476757a5
```
# local
bin/spark-submit [--master local]
bin/spark-submit --master local-cluster[2,3,1024]

# standalone(start master/slave firstly)
bin/spark-submit --master spark://wl1:7077 [--deploy-mode client]
bin/spark-submit --master spark://wl1:7077 --deploy-mode cluster

# based on yarn
bin/spark-submit --master [--deploy-mode client]
bin/spark-submit --master --deploy-mode cluster
```
## test task
1. by shell command
```sh
cd <spark-home-dir>
bin/spark-submit --class org.apache.spark.examples.SparkPi --master yarn --deploy-mode client ./examples/jars/spark-examples_2.11-2.4.0.jar 50
```
2. by scala shell
```
sc.textFile("hdfs://master.com/input/seleniumlibrary.txt").flatMap(_.split("")).map((_,1)).reduceByKey(_+_).sortBy(_._2,false).saveAsTextFile("hdfs://master.com/output/selenium-results.txt")
```
## issues
1. spark on yarn提交任务时报ClosedChannelException解决方案: https://www.cnblogs.com/pojishou/p/6358588.html
