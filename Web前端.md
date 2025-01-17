# 一、请求响应

## 1.postman

![image-20240913095142070](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240913095142070.png)

## 2.各类参数响应

### 简单参数：

![image-20240913095349585](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240913095349585.png)

![image-20240913100136833](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240913100136833.png)

![image-20240913100522962](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240913100522962.png)

![image-20240913101316153](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240913101316153.png)

### 实体参数：![image-20240913101339864](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240913101339864.png)

![image-20240913101459350](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240913101459350.png)

### 数组集合参数：![image-20240913101534075](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240913101534075.png)

![image-20240913101551424](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240913101551424.png)

![image-20240913101614301](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240913101614301.png)

### 日期参数：![image-20240913101631127](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240913101631127.png)

### Json参数：![image-20240913101715827](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240913101715827.png)

### 路径参数：

![image-20240913101743749](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240913101743749.png)

## 3.常见响应状态码

![image-20240910152256865](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240910152256865.png)

状态码大全：https://cloud.tencent.com/developer/chapter/13553

# 二、分层解耦

## 分层解耦

![image-20240913101957918](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240913101957918.png)

1.三层架构：控制层（接受请求和响应数据/controller）、逻辑层（逻辑处理/service）、数据层（数据访问操作，如增删改查/dao）

![image-20240913101906177](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240913101906177.png)

DAO：

![image-20240911110213429](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911110445022.png)

![image-20240911110556005](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911110556005.png)



Service：![image-20240911110643647](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911110643647.png)

![image-20240911110803455](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911110803455.png)

![image-20240911110828474](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911110828474.png)

Controller：![image-20240911110938064](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911110938064.png)

2.分层解耦

控制反转：IOC。对象的创建控制权由程序自身转移到外部（容器），这种思想称为控制反转。

依赖注入：DI。容器为应用程序提供运行时，所依赖的资源，称为依赖注入。

Bean对象：IOC容器中创建、管理的对象，称为bean。

![image-20240911114029906](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911114029906.png)

![image-20240911115730404](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911115730404.png)

![image-20240911134736708](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911134736708.png)

# 三、数据库

## DDL

![](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911135936388.png)

![image-20240911142233007](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911142233007.png)

![image-20240911142604055](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911142604055.png)

![image-20240911142620257](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911142620257.png)

![image-20240911142630370](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911142630370.png)

## 示例

![image-20240911143601078](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911143601078.png)

![image-20240911143711494](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911143711494.png)

![](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911144925790.png)

![image-20240911144648670](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911144648670.png)

## DML

![image-20240911145038246](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911145038246.png)

![image-20240911145319391](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911145319391.png)

![image-20240911145340482](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911145340482.png)

## DQL

![image-20240911145928562](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911145928562.png)

![image-20240911145826364](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911145826364.png)

![](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911145852849.png)

![image-20240911145905025](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911145905025.png)

![image-20240911150011555](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911150011555.png)

![image-20240911150734242](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911150734242.png)



![image-20240911150916141](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911150916141.png)

![image-20240911150842488](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911150842488.png)

![image-20240911150826457](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911150826457.png)

![image-20240911151257069](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911151257069.png)

![image-20240911151315392](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911151315392.png)

![image-20240911151929339](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911151929339.png)

![image-20240911151743419](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911151743419.png)

![image-20240911152925300](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911152925300.png)

![image-20240911153204409](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911153204409.png)

![image-20240911153432243](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911153432243.png)

### 外键约束

![image-20240911155828420](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911155828420.png)

![image-20240911155923195](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911155923195.png)

![image-20240911160304249](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911160304249.png)

![image-20240911160936015](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911160936015.png)

### 内连接和外连接

![image-20240911163759797](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911163759797.png)

![image-20240911163819578](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911163819578.png)

![image-20240911163850691](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911163850691.png)

![image-20240911164125553](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911164125553.png)

![image-20240911164310640](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911164310640.png)

### 子查询

![image-20240911164448364](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911164448364.png)

![image-20240911164509768](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911164509768.png)

![image-20240911164637512](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911164637512.png)

![image-20240911164811430](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911164811430.png)

![image-20240911164824983](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911164824983.png)

![image-20240911164903338](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911164903338.png)

![image-20240911164953956](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911164953956.png)

![image-20240911165126022](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911165126022.png)

![image-20240911165144252](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911165144252.png)

![image-20240911165208653](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911165208653.png)

![image-20240911170243390](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911170243390.png)

![image-20240911170249888](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911170249888.png)

### 事务

![image-20240911170300629](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911170300629.png)

提交事务前，命令有误，可通过rollback将执行命令回退。

![image-20240911170358795](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911170358795.png)

![image-20240911170432769](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911170432769.png)

![image-20240911172130074](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911172130074.png)

![image-20240911172353698](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911172353698.png)

![image-20240912151659165](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912151659165.png)

![image-20240912152318954](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912152318954.png)

![image-20240912154255567](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912154255567.png)

![image-20240912154313158](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912154313158.png)

# 四、MyBatis

## 1.IDEA创建mybatis

![image-20240911173259429](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240911173259429.png)

## 2.LomBok

![image-20240912091554826](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912091554826.png)

## 3.增删改查

执行增删改查操作时，要在public上面加上注解@Delete（“delete from 表名 where 字段名 = #{字段名}”）（根据功能，替换为相应的注解，动态实现删除功能）

![image-20240912092208125](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912092208125.png)

![image-20240912093445484](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912093445484.png)

![img](file:///C:\Users\1\AppData\Roaming\feiq\RichOle\1536197199.bmp)

![image-20240912101010062](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912101010062.png)

![image-20240912101912267](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912101912267.png)

![image-20240912102500823](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912102500823.png)

![image-20240912103332453](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912103332453.png)

![image-20240912104106337](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912104106337.png)

![image-20240912105551904](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912105551904.png)

## 4.XML

注解可以用来映射简单语句，但是复杂语句，最好使用XML来映射。

![image-20240912110948482](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912110948482.png)

![image-20240912111517954](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912111517954.png)

## 5.动态SQL

![image-20240912115051495](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912115051495.png)

![image-20240912120007589](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912120007589.png)

![image-20240912120025252](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912120025252.png)

![image-20240912135835885](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912135835885.png)

![image-20240912140212025](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912140212025.png)

![image-20240912140247011](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912140247011.png)

## 6.示例

![image-20240912140824722](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912140824722.png)

![image-20240912141521417](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912141521417.png)

**开发流程：**

![image-20240912141544694](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912141544694.png)

**配置：**

![image-20240912142224397](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912142224397.png)

![image-20240912142920055](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912142920055.png)

![image-20240912142950955](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912142950955.png)

![image-20240912145230746](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912145230746.png)

![image-20240912150137775](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912150137775.png)

![image-20240912150147952](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912150147952.png)

# 五、AOP

## AOP

![image-20240912155846395](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912155846395.png)

![image-20240912155647943](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912155647943.png)

示例：

![image-20240912160047302](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912160047302.png)

![image-20240912160230778](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912160230778.png)

![image-20240912160547714](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912160547714.png)

![image-20240912160703241](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912160703241.png)

![image-20240912160959083](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912160959083.png)

![image-20240912161924947](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912161924947.png)

![image-20240912162207208](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912162207208.png)

![image-20240912162708172](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912162708172.png)

## 切入点表达式

![image-20240912164341856](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912164341856.png)

![image-20240912164418329](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912164418329.png)

![image-20240912164651991](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912164651991.png)

![image-20240912165514977](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912165514977.png)

![image-20240912165455530](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912165455530.png)

![image-20240912165851661](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912165851661.png)

## 示例

![image-20240912170014205](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912170014205.png)

# 六、Spring Boot

## Spring Boot

![image-20240912172202454](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912172202454.png)

![image-20240912172259000](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912172259000.png)

![image-20240912172552197](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912172552197.png)

![image-20240912173912897](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912173912897.png)

## Bean

![image-20240912174602082](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912174602082.png)

![image-20240912174647530](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912174647530.png)

![image-20240912174707781](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912174707781.png)

![image-20240912174756825](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912174756825.png)

![image-20240912175208333](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240912175208333.png)

![image-20240913085006142](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240913085006142.png)

# 七、Tomcat

![image-20240913092708689](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240913092708689.png)

## 常见问题

![image-20240913092802323](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240913092802323.png)

![image-20240913093226931](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240913093226931.png)

![image-20240913093516314](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240913093516314.png)

![image-20240913093548338](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240913093548338.png)

![image-20240913093631502](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240913093631502.png)

# 八、Web入门程序解析

![image-20240913093831697](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240913093831697.png)

![image-20240913094527315](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240913094527315.png)