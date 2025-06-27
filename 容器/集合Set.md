# 集合 Set
> 集合的性质：唯一性 && 无序性

- `HashSet` 和 `TreeSet` 都实现了 `Set` 接口

## 1. HashSet
```java
var badWords = new HashSet<String>();
badWords.add("sex");
badWords.add("drugs");
badWords.add("c++");

if (badWords.contains(username.toLowerCase())) {
  System.out.printf("please choose a different user name");
}
```

## 2. TreeSet
- `TreeSet` 可以按排序顺序遍历集合  
- `TreeSet` 类实现了 `SortedSet` 接口 和 `NavigableSet` 接口  
- 集合元素类型必须实现 `Comparable` 接口，或者在构造器中提供 `Comparator` 方法  
1. 集合元素类型实现 `Comparable` 接口
```java
// 自定义类实现 Comparable 接口
class Person implements Comparable<Person> {
    private String name;
    private int age;
    
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    @Override
    public int compareTo(Person other) {
        // 先按年龄排序，年龄相同再按姓名排序
        if (this.age != other.age) {
            return Integer.compare(this.age, other.age);
        }
        return this.name.compareTo(other.name);
    }
    
    @Override
    public String toString() {
        return name + "(" + age + ")";
    }
}

public class TreeSetExample1 {
    public static void main(String[] args) {
        TreeSet<Person> people = new TreeSet<>();
        
        people.add(new Person("Alice", 25));
        people.add(new Person("Bob", 30));
        people.add(new Person("Charlie", 20));
        people.add(new Person("David", 25)); // 与Alice同龄但名字不同
        
        // 自动按年龄和姓名排序
        for (Person p : people) {
            System.out.println(p);
        }
    }
}

----------------------------------------------------------------------------
输出：
Charlie(20)
Alice(25)
David(25)
Bob(30)
```
2. 在构造器中提供 `Comparator` 方法
```java
class Product {
    private String name;
    private double price;
    
    public Product(String name, double price) {
        this.name = name;
        this.price = price;
    }
    
    public String getName() { return name; }
    public double getPrice() { return price; }
    
    @Override
    public String toString() {
        return name + ": $" + price;
    }
}

public class TreeSetExample2 {
    public static void main(String[] args) {
        // 使用Comparator按价格排序
        TreeSet<Product> products = new TreeSet<>(new Comparator<Product>() {
            @Override
            public int compare(Product p1, Product p2) {
                return Double.compare(p1.getPrice(), p2.getPrice());
            }
        });

        products.add(new Product("Laptop", 999.99));
        products.add(new Product("Phone", 699.99));
        products.add(new Product("Tablet", 399.99));
        products.add(new Product("Monitor", 199.99));
        
        // 自动按价格排序
        for (Product p : products) {
            System.out.println(p);
        }
    }
}

----------------------------------------------------------------------------
输出：
Monitor: $199.99
Tablet: $399.99
Phone: $699.99
Laptop: $999.99
```