# 为什么重写equals时必须重写hashCode方法？


* 因为两个相等的对象的`hashCode`值必须是相等。
* 也就是说如果`equals`方法判断两个对象是相等的，那这两个对象的`hashCode`值也要相等。
* 如果重写`equals()`时没有重写`hashCode()`方法的话就可能会导致`equals`方法判断是相等的两个对象,`hashCode`值却不相等。


---

> 作者: hahaen  
> https://hahaen.github.io/%E4%B8%BA%E4%BB%80%E4%B9%88%E9%87%8D%E5%86%99equals%E6%97%B6%E5%BF%85%E9%A1%BB%E9%87%8D%E5%86%99hashcode%E6%96%B9%E6%B3%95/
