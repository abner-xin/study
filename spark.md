## job history
https://blog.csdn.net/stark_summer/article/details/46459701

## running mode
https://www.jianshu.com/p/65a3476757a5

## test task
```sh
cd <spark-home-dir>
bin/spark-submit --class org.apache.spark.examples.SparkPi --master yarn --deploy-mode client ./examples/jars/spark-examples_2.11-2.4.0.jar 50
```

## issues
1. spark on yarn提交任务时报ClosedChannelException解决方案: https://www.cnblogs.com/pojishou/p/6358588.html
