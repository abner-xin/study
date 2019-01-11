## test command
```sh
cd <hadoop-home-dir>
bin/hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-2.9.0.jar wordcount /input /output
```

## kill a running job
```
yarn application -kill application_1546618751159_0031
```

## view node disk usage
```
hdfs dfsadmin -report
```
