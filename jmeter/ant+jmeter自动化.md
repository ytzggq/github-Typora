jmeter -n -t D:\Software\softwarePackage\apache-jmeter-5.1\bin\28_180_4.jmx -l testLogFile1 -e -o ./outputtest

使用Jmeter ServerAgent插件监控阿里云服务器时，默认端口为4444，连接不上。修改端口号为7878后正常。

修改端口命令：java -jar ./CMDRunner.jar --tool PerfMonAgent --udp-port 7879 --tcp-port 7879



在jmeter的bin目录上打开cmd。并且需要把脚本放在bin目录下：

jmeter -n -t D:\Software\softwarePackage\apache-jmeter-5.1\bin\xiangchudianfan.jmx -l xingchuLog1 -e -o ./xingchu1

