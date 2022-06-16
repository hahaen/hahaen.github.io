# 集合


[集合](https://segmentfault.com/a/1190000040177363)

## 常见的集合有哪些？

* Java集合类主要由两个根接口`Collection`和`Map`派生出来的 
* Collection派生出了三个子接口：`List、Set、Queue`（Java5新增的队列）
* 因此Java集合大致也可分成`List、Set、Queue、Map`四种接口体系。

**注意：**Collection是一个接口，Collections是一个工具类，Map不是Collection的子接口。

![集合](/img/集合/img.png)

* `List`代表了有序可重复集合，可直接根据元素的索引来访问
* `Set`代表无序不可重复集合，只能根据元素本身来访问
* `Queue`是队列集合 
* `Map`代表的是存储key-value对的集合，可根据元素的`key`来访问`value`

## 线程安全的集合有哪些？线程不安全的呢？

线程安全的：

* Hashtable：比HashMap多了个线程安全。 
* ConcurrentHashMap:是一种高效但是线程安全的集合。 
* Vector：比Arraylist多了个同步化机制。 
* Stack：栈，也是线程安全的，继承于Vector。

线性不安全的：

* HashMap 
* Arraylist 
* LinkedList 
* HashSet 
* TreeSet 
* TreeMap


