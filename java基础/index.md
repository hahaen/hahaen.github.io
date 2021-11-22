# Java基础

## Java程序的运行原理

.java --- 编译(compler) --- 字节码(.class) --- JVM

* .class 打包成 .jar
* JVM解析字节码

1. 使用文字编辑软件或集成开发环境编辑 Java 源文件，扩展名为 .java 
2. 通过编译 .java 文件，生成同名的 .class 字节码文件 
3. 通过 JVM 解释方式，将 .class 字节码文件转变为由 0 或 1 组成的二进制指令（机器码）运行

## JDK/JRE有什么区别？

JDK=JRE+javac

* javac 相当于 编译compler
* jdk java开发工具包,java语言编写的程序所需的开发工具包
* jre java运行时环境,即java程序的运行时环境，包含了java虚拟机，java基础类库

jdk包含jre,jre是java运行时环境，另外jdk包含开发时所需要的sdk和编译器javac和javadoc工具

## Java的基本类型？

基本数据类型是CPU可以直接进行运算的类型。Java定义了以下几种基本数据类型：

* 整数类型：byte，short，int，long 
* 浮点数类型：float，double 
* 字符类型：char 
* 布尔类型：boolean

String是基本数据类型吗？答：不是

## Java的参数传递是传值还是传引用？

* Java世界中的一切对象都是指针(地址)
* 函数调用永远是传值

1. 基本类型（包括String类）作为参数传递时，是传递值的拷贝，无论你怎么改变这个拷贝，原值是不会改变的
2. 引用类型（包括数组，对象以及接口）作为参数传递时，是把对象在内存中的地址拷贝了一份传给了参数。
* 注意：基本数据类型的封装类Integer、Short、Float、Double、Long、Boolean、Byte、Character虽然是引用类型，但它们在作为参数传递时，也和基本数据类型一样，是值传递。

## **StringBuffer/StringBuilder**

### 区别

* StringBuffer更快，但线程不安全，常用
* StringBuilder稍慢，但线程安全

### 线程安全性

* 如果没有额外声明，所有类的默认都是线程不安全的

## Object有哪些方法？

Object类，属于java.lang包，位于类层次结构树的顶部。
每个类都是Object类的直接或间接的后代。
使用或编写的每个类都继承Object的实例方法。

常用方法：

* `getClass 方法` final 方法、获取对象的运行时 class 对象，class 对象就是描述对象所属类的对象。
* `hashCode 方法` 该方法主要用于获取对象的散列值。Object 中该方法默认返回的是对象的堆内存地址。
* `equals 方法` 该方法用于比较两个对象，如果这两个对象引用指向的是同一个对象，那么返回 true，否则返回 false。
* `clone 方法` 该方法是保护方法，实现对象的浅复制，只有实现了 Cloneable 接口才可以调用该方法，否则抛出 CloneNotSupportedException 异常。
* `toString 方法` 返回一个 String 对象，一般子类都有覆盖。默认返回格式如下：对象的 class 名称 + @ + hashCode 的十六进制字符串。
* `wait 方法` 当timeout 为 0，即不等待。

## String中有哪些方法？

常用方法：

* `indexOf()` 返回指定字符的索引。 
* `charAt()` 返回指定索引处的字符。 
* `replace()` 字符串替换。 
* `trim()` 去除字符串两端空白。 
* `split()` 分割字符串，返回一个分割后的字符串数组。 
* `getBytes()` 返回字符串的 byte 类型数组。 
* `length()` 返回字符串长度。 
* `toLowerCase()` 将字符串转成小写字母。 
* `toUpperCase()` 将字符串转成大写字符。 
* `substring()` 截取字符串。 
* `equals()` 字符串比较。

