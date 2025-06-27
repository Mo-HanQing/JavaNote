# 迭代器 Iterator
> 迭代器 `Iterator` 用于对集合进行遍历操作

## 1. Iterator
`Collection` 的超接口 `Iterable<T>` 中定义了 `Iterator<T> iterator()` 方法，该方法能够生成一个迭代器

```java
public interface Iterator<E> {
    boolean hasNext();  // 检查是否还有元素
    E next();           // 获取下一个元素
    void remove();      // 删除当前元素（可选操作）
}
```
### 使用示例
```java
List<String> list = new ArrayList<>();
list.add("Java");
list.add("Python");
list.add("C++");

Iterator<String> iterator = list.iterator();

while(iterator.hasNext()) {
  String language = iterator.next();
  System.out.println(language);

  if (language.equals("C++")) {
    iterator.remove();
  }
}
```

## 2. ListIterator
> `ListIterator` 接口是 `Iterator`的子接口

```java
public interface ListIterator<E> extends Iterator<E> {
    boolean hasPrevious();  // 是否有前一个元素
    E previous();          // 返回前一个元素
    int nextIndex();       // 返回下一个元素的索引
    int previousIndex();   // 返回前一个元素的索引
    void set(E e);         // 替换当前元素
    void add(E e);         // 添加元素
}
```

### 使用示例
```java
List<String> list = Arrays.asList("Java", "Python", "C++");

ListIterator<String> listIterator= list.listIterator();

/*
add(E e) 将指定元素插入列表中
新元素会被插入到下一次调用 next() 返回的元素之前
或者下一次调用 previous() 返回的元素之后
*/

// 在第一个元素前添加
listIterator.add("Php");
// 移动到第二个位置
listIterator.next(); // 现在指向“Java”

// 正向遍历
while (listIterator.hasNext()) {
  String element = listIterator.next();
  if (element.equals("C++")) {
    listIterator.set("C#");
  }
}

// 反向遍历
while (listIterator.hasPrevious()) {
  Stirng element = listIterator.previous();
  if (element.equals("Python")) {
    listIterator.set("C");
  }
}
```