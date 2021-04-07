## 1、邮件配置

Jenkins配置自动发送邮件  https://www.cnblogs.com/gcgc/p/5631385.html

1.开通QQ的SMTP服务，需要发一条短信，qq会给你一个密码（不是你的QQ邮箱密码哦）

 2.安装 [Email Extension Plugin](http://wiki.jenkins-ci.org/display/JENKINS/Email-ext+plugin) 插件

 

3.进入系统管理--系统设置

3.1按照如下图设置

![img](https://images2015.cnblogs.com/blog/867526/201607/867526-20160701120021624-26429151.png)

3.2然后找到 **邮件通知**  并按照如下设置

![img](https://images2015.cnblogs.com/blog/867526/201606/867526-20160630214101968-1469756962.png)

3.3最后必须设置 **Jenkins Location**  如下图

上面只是配置邮件服务器地址、账号和密码，但是jenkins不知道采用哪个邮箱去发送，系统管理员邮件地址必须与上图设置的用户保持一致。
此时我们已经可以发送邮件了



![img](https://images2015.cnblogs.com/blog/867526/201606/867526-20160630214131906-344081859.png)

4.在job中增加构建后操作 **Editable Email Notification**

　　**其实最后的邮件内容是由\**Editable Email Notification步骤里面的【Advanced setting】的Triggers里面的【高级】来决定的\****

 

![img](https://images2015.cnblogs.com/blog/867526/201606/867526-20160630215950874-1483467386.png)

![img](https://images2015.cnblogs.com/blog/867526/201607/867526-20160701130837171-1483733533.png)

高级里面可以配置什么情况下发邮件，如下图

![img](https://images2015.cnblogs.com/blog/867526/201606/867526-20160630215802374-1664790933.png)





## 2、构建项目

**1、进入项目配置界面**

进入新建的项目界面，点击配置按钮，进入系统配置页面：







## 3、[jenkins关闭，重启几种方式](https://www.cnblogs.com/ninefish/p/9816612.html)

**一.以服务形式实现安装启动的的jenkins（如mis包直接安装）**

1.关闭Jenkins

  只需要在访问jenkins的网站后面加上exit即可。如访问的地址是 http://192.168.240.179:8080/，那只要浏览器输入**http://192.168.240.179:8080/exit**即可退出，或者**http://localhost:8080/exit**

2.重启Jenkins

**同理：http://192.168.240.179:8080/restart**

3.重新加载配置

 **http://192.168.240.179:8080/reload**

