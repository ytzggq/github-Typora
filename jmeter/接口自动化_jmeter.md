###### 一、接口自动化

1、增加配置元件---请求默认值

![image-20200325162745919](../Untitled 3.assets/image-20200325162745919.png)

2、如果有参数关联要求token，配置元件---请求头  ，token参数化

<img src="../Untitled 3.assets/image-20200325163014742.png" alt="image-20200325163014742" style="zoom: 200%;" />





然后再加一个

3、逻辑控制器—循环控制器

![image-20200325163205036](../Untitled 3.assets/image-20200325163205036.png)



3.1再循环控制器下，增加配置元件-CSVdata 

![image-20200325163329267](../Untitled 3.assets/image-20200325163329267.png)

这里的文件名就是对于CSV的路径

参数按照再CSV的顺序填写

![image-20200325163630824](../Untitled 3.assets/image-20200325163630824.png)

3.2再循环控制器增加 如果（If）控制器_优先级

${__jexl3("${Prority}"=="H")}

![image-20200325163953294](../Untitled 3.assets/image-20200325163953294.png)



3.2.1 如果（If）控制器_优先级 下增加  两个“如果（if）控制器”  get和post请求

![image-20200325164049505](../Untitled 3.assets/image-20200325164049505.png)

${__jexl3("${protocal}"=="GET")}

![image-20200325164103877](../Untitled 3.assets/image-20200325164103877.png)

${__jexl3("${protocal}"=="POST")}

增加post请求，都是参数化

![image-20200325164145438](../Untitled 3.assets/image-20200325164145438.png)

如果有接口需要关联，正则表达式

![image-20200325164301643](../Untitled 3.assets/image-20200325164301643.png)

响应信息

![image-20200325164457317](../Untitled 3.assets/image-20200325164457317.png)![image-20200325164345722](../Untitled 3.assets/image-20200325164345722.png)





执行后，都通过

![image-20200325164603548](../Untitled 3.assets/image-20200325164603548.png)



###### 二、注意

也可以通过ant+jmeter构建自动化报告

1、随便建一个文件，然后把build.xml  和脚本放在文件里面

![image-20200325164724583](../Untitled 3.assets/image-20200325164724583.png)

2、打开dos命令

输入：ant

![image-20200325164902065](../Untitled 3.assets/image-20200325164902065.png)

3、输出结果

![image-20200325164931563](../Untitled 3.assets/image-20200325164931563.png)

4、查看结果

![image-20200325165239277](../Untitled 3.assets/image-20200325165239277.png)









三、另外一种结果，再研究

