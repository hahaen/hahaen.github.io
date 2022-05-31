# 静态方法和实例方法有何不同？

### 调用方式

* 在外部调用静态方法时，可以使用`类名.方法名`的方式，也可以使用`对象.方法名`的方式，而实例方法只有后面这种方式。也就是说，**调用静态方法可以无需创建对象**。 
* 不过，需要注意的是一般不建议使用`对象.方法名`的方式来调用静态方法。这种方式非常容易造成混淆，静态方法不属于类的某个对象而是属于这个类。

因此，一般建议使用`类名.方法名`的方式来调用静态方法。

```java
public class Person {
    public void method() {
      //......
    }

    public static void staicMethod(){
      //......
    }
    
    public static void main(String[] args) {
        Person person = new Person();
        // 调用实例方法
        person.method();
        // 调用静态方法
        Person.staicMethod()
    }
}
```

### 访问类成员是否存在限制

* 静态方法在访问本类的成员时，只允许访问静态成员（即静态成员变量和静态方法），不允许访问实例成员（即实例成员变量和实例方法），而实例方法不存在这个限制。

---

> 作者: hahaen  
> https://hahaen.github.io/%E9%9D%99%E6%80%81%E6%96%B9%E6%B3%95%E5%92%8C%E5%AE%9E%E4%BE%8B%E6%96%B9%E6%B3%95%E6%9C%89%E4%BD%95%E4%B8%8D%E5%90%8C/
