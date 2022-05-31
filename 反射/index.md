# 反射

## 什么是反射？

将类的各个组成部分封装为其他对象的过程就叫做`反射`，
其中 `组成部分` 指的是我们类的 `成员变量（Field）`、`构造方法（Constructor）`、`成员方法（Method）`。

## 使用反射的优缺点?

**优点:**

* 在程序运行过程中可以操作类对象，增加了程序的灵活性
* 解耦，从而提高程序的可扩展性，提高代码的复用率，方便外部调用
* 对于任何一个类，当知道它的类名后，就能够知道这个类的所有属性和方法；而对于任何一个对象，都能够调用它的一个任意方法

**缺点：**

* 性能问题：Java 反射中包含了一些动态类型，JVM 无法对这些动态代码进行优化，
因此通过反射来操作的方式要比正常操作效率更低。 
* 安全问题：使用反射时要求程序必须在一个没有安全限制的环境中运行，
如果程序有安全限制，就不能使用反射。 
* 程序健壮性：反射允许代码执行一些平常不被允许的操作，破坏了程序结构的抽象性，
导致平台发生变化时抽象的逻辑结构无法被识别。

## 反射机制的作用

* 反编译：.class-->.java 
* 通过反射机制访问java对象的属性，方法，构造方法等；

## 反射创建api

* `getDeclaredMethods []`  获取该类的所有方法 
* `getReturnType()`        获取该类的返回值 
* `getParameterTypes()`    获取传入参数 
* `getDeclaredFields()`    获取该类的所有字段 
* `setAccessible`          允许访问私有成员

实现方式：
1. 调用运行时类本身的.class属性 
2. 利用运行时类的对象获取（getclass()） 
3. 通过类的静态方法获取 
4. 通过类的加载器

## 获取 Class 对象的方式

### Class.forName("全类名")

源代码阶段，它能将字节码文件加载进内存中，然后返回 Class 对象，
多用于配置文件中，将类名定义在配置文件中，通过读取配置文件来加载类。

### 类名.class

类对象阶段，通过类名的 class 属性来获取，多用于参数的传递。

### 对象.getClass()

运行时阶段，`getClass()` 定义在 `Object` 类中，表明所有类都能使用该方法，多用于对象的获取字节码的方式。

定义一个 Person 类，用于后续反射功能的测试:

```java
 public void setScore(float score) {
        this.score = score;
    }

    public int getRank() {
        return rank;
    }

    public void setRank(int rank) {
        this.rank = rank;
    }

    @Override
    public String toString() {
        final StringBuffer sb = new StringBuffer("Person{");
        sb.append("age=").append(age);
        sb.append(", name='").append(name).append('\'');
        sb.append(", id=").append(id);
        sb.append(", grade=").append(grade);
        sb.append(", score=").append(score);
        sb.append(", rank=").append(rank);
        sb.append('}');
        return sb.toString();
    }
}
```

定义好 Person 类之后，我们尝试用 3 种不同的方式来获取 Class 对象

```java
public class Demo1 {
    public static void main(String[] args) throws ClassNotFoundException {
//        第一种方式，Class.forName("全类名")
        Class class1 = Class.forName("com.hahaen.Person");
        System.out.println(class1);

//        第二种方式，类名.class
        Class class2 = Person.class;
        System.out.println(class2);

//        第三种方式，对象.getName()
        Person person = new Person();
        Class class3 = person.getClass();
        System.out.println(class3);

//        比较三个对象是否相同
        System.out.println(class1 == class2);
        System.out.println(class1 == class3);
    }
}
```

```java
        com.hahaen.Person
        com.hahaen.Person
        com.hahaen.Person
        true
        true
```

比较结果返回的是两个 true，
说明通过上述三种方式获取的 Class 对象都是同一个，**同一个字节码文件（*.class）在一次运行过程中只会被加载一次**。



---

> 作者: hahaen  
> https://hahaen.github.io/%E5%8F%8D%E5%B0%84/
