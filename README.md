# String-通配符
### 用途
 在安卓开发规范中是不允许Java代码中出现中文，所以出现如下面的情况：
 ```java
 
   TransferDetailsEntity detailsEntity = new TransferDetailsEntity();
   TextView txtMarkContent.setText("借款原因：" + detailsEntity.getSummary());
   
```
 通配符允许我们在String.xml文件中建立一个模板，在需要的时候替换其中特点的字段，先介绍下通配符是怎么解决上面问题的
 
###通配符
#####基本用法
   %n$ms：代表输出的是字符串，n代表是第几个参数，设置m的值可以在输出之前放置空格 
   
   %n$md：代表输出的是整数，n代表是第几个参数，设置m的值可以在输出之前放置空格，也可以设为0m,在输出之前放置m个0 
   
   %n$mf：代表输出的是浮点数，n代表是第几个参数，设置m的值可以控制小数位数，如m=2.2时，输出格式为00.00 
   
 也可简单写成：
 
   %d   （表示整数）
   
   %f    （表示浮点数）
   
   %s   （表示字符串）
   
 上面的问题可以这样解决：
  ```java
    <String name = "headTitle">借款原因：%1$s</String>
  ```
  ```java
    String sAgeFormat = getResources().getString(R.string.headTitle);  
    String.format(sAgeFormat, detailsEntity.getSummary());
  ```
  
  如果想实现多个String的替换
   ```java
    <String name = "headTitle">借款原因：%1$s 借款时间：%2$s</String>
   ```
   ```java
    String lastResult = getResources().getString(R.string.headTitle);  
    String.format(lastResult, detailsEntity.getSummary(),detailsEntity.getTime());
   ```
  
