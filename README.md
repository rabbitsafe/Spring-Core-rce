Spring Core RCE 命令执行和webshell写入

3.29网上爆出Spring核弹级漏洞：Spring Core RCE，可写入webshell，可命令执行

网上打码的利用截图
![image](https://github.com/rabbitsafe/Spring-Core-rce/blob/main/poc.png)


利用网上搭建的漏洞环境进行漏洞复现

docker pull vulfocus/spring-core-rce-2022-03-29:latest

在8888端口上开启spring

docker run -p 8888:8080 --name vulnerable-app vulnerable-app
![image](https://github.com/rabbitsafe/Spring-Core-rce/blob/main/poc1.jpg)

利用spring-core-rce.py进行漏洞验证，直接修改tomcat日志配置信息和写入webshell
![image](https://github.com/rabbitsafe/Spring-Core-rce/blob/main/poc2.jpg)

利用写入的webshell执行系统命令
![image](https://github.com/rabbitsafe/Spring-Core-rce/blob/main/poc3.jpg)

漏洞影响：
jdk 版本在9及以上的
使用了Spring Framework或衍生框架


漏洞修复建议：
目前，Spring 官方暂未发布补丁，建议降低jdk 版本作为临时方案
