# 映射 Map
> 映射 `Map` ：存储键值对


## Map 的主要实现类
- HashMap - 基于哈希表实现，无序，允许 null 键和 null 值
- LinkedHashMap - 保持插入顺序或访问顺序
- TreeMap - 基于红黑树实现，按键的自然顺序或 Comparator 排序


## 基本方法
```java
// 创建Map
Map<String, Integer> map = new HashMap<>();

// 添加元素
map.put("apple", 15);
map.put("apple", 10); // 会将值更新为 10
map.putIfAbsent("banana", 5); // 只有键不存在时才放入

// 移除元素
map.remove("orange");

// 获取元素
map.get("apple"); // 如果键不存在则返回 null
map.getOrDefault("apple", 10); // 如果键不存在则返回 10

// 检查键是否存在
map.containsKey("pear");

// 遍历 1
for (Map.Entry<String, Integer> entry : map.entrySet()) {
  System.out.println(entry.getKey() + ":" + entry.getValue);
}

// 遍历2
for (String key : map.keySet()) {
  System.out.println(key + ":" + map.get(key));
}

// 遍历3
map.forEach((k, v) -> Syatem.out.println(k + ":" + v));

// compute 计算新值
map.compute("apple", (k, v) -> v + 5); // 值从 10 变为 15

// merge 合并值
map.merge("apple", 3, Integer::sum) // 值从 15 变为 18

// replaceAll 替换所有值
map.replaceAll((k, v) -> v * 2) // 所有值乘 2
```

## 解释
```java
Map.Entry<String, Integer> entry : map.entrySet()
```
- `map.entrySet()`:
  - 返回一个 `Set<Map.Entry<K,V>>` 集合
  - 包含 `Map` 中所有的键值对（每个键值对都是一个 `Map.Entry` 对象）
  
- `Map.Entry<String, Integer>`:
  - 表示一个泛型键值对接口
  - 这里指定键是 String 类型，值是 Integer 类型

- 每个 `Map.Entry` 对象包含：
  - `getKey()`   - 获取键
  - `getValue()` - 获取值
  - `setValue()` - 设置值

