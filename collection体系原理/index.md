# Collection体系原理

## Collection体系简介
### list
有序可重复，最常用的是 ArrayList，实际就是一个数组
```
Collection<Integer> c = new LinkedHashSet<>();
        
// IntegerList
List<Integer> list = new ArrayList<>(c);
        
// 等价于
List<Integer> list2 = new ArrayList<>();
list2.addAll(c);
        
// 等价于
List<Integer> list3 = new ArrayList<>();
for (Integer i : c) {
    list3.add(i);
}
```
### Set
无序且不可重复的元素集合。

只是简单通过object.contains()判断添加新元素时是否重复，从而实现去重的 Set 是很低效的，这就引出了对象的 hashcode。

### Java世界第⼆重要的约定
hashCode:
1. 同⼀个对象必须始终返回相同的 hashCode 
2. 两个对象的 equals 返回 true，必须返回相同的 hashCode 
3. 两个对象不等，也可能返回相同的 hashCode
   
### HashSet
HashSet 是无序的，是最常用的 Set 实现。
可以利用 set 为 list 过滤去重：
```angular2html
List<Integer> list = new ArrayList<>();

list.add(2);
list.add(3);
list.add(4);
list.add(3);
        
Set<Integer> set = new HashSet<>(list); 
```
LinkedHashSet 是有序的，顺序就是插入元素时的顺序。
### Collections ⼯具⽅法集合
* emptySet(): 等返回⼀一个⽅方便便的空集合 
* synchronizedCollection: 将⼀一个集合变成线程安全的 
* unmodifiableCollection: 将⼀一个集合变成不不可变的（也可以使⽤用Guava的Immutable）
## Map 体系
map 是 一个将 keys 映射到 values 的对象，键不能重复，每个键只能映射一个值，值可以重复。 <br>
* `keySet()`返回键的集合，因为键不可重复，所以可以返回一个 set； <br>
* `values()`返回值的集合，因为值可以重复，所以返回的是 collection。 <br>
注意：`keySet()`和 `map`背后的 keys 是同一组数据，所以二者的修改会相互影响。 <br>
<br>
### HashMap
* HashMap 是最常用、最高效的 Map 实现。 
* HashMap 的扩容，思路同样是创建更大的空间，然后把之前的数据 copy 进来。 
* HashMap 是多线程不安全的，可使用 ConcurrentHashMap。<br>

Java 7 开始会采用[红黑树](https://zh.wikipedia.org/wiki/%E7%BA%A2%E9%BB%91%E6%A0%91)代替链表

HashMap 和 HashSet 本质上是同一个东西：<br>
HashMap 的 key 集合（set）就是 HashSet，而 HashSet 内部其实就是个 HashMap，毕竟 HashSet 拥有的功能 HashMap 都有。
### 有序集合TreeSet/TreeMap
TreeSet 可以排序（默认是自然顺序）。<br>
HashSet、LinkedHashSet 与 TreeSet 对比：
```angular2html
public class Main {

    public static void main(String[] args) {
        List<Integer> list = Arrays.asList(1000, -13, 0, -41656, 1250, 555);

        Set set1 = new HashSet<>(list);
        Set set2= new LinkedHashSet(list);
        Set set3 = new TreeSet(list);

        System.out.println(set1);
        System.out.println(set2);
        System.out.println(set3);
    }
}

[0, 1250, -41656, 1000, 555, -13]
[1000, -13, 0, -41656, 1250, 555]
[-41656, -13, 0, 555, 1000, 1250]
```
TreeMap 同理
## Guava
* 不要重复发明轮⼦子！尽量量使⽤用经过实战检验的类库 
* Lists/Sets/Maps 
* ImmutableMap/ImmutableSet 
* Multiset/Multimap
* BiMap!12
---
## Collection体系简介图
![Collection体系](/img/Collection体系.png)<br>






