**Set接口是继承Collection接口的子接口**

HashSet、LinkedHashSet 和 TreeSet 都是 Set 接口的实现类，都能保证元素唯一，并且都不是线程安全的。

#### HashSet

- **特点**

  - 无序：HashSet 不保证元素的插入顺序。
  - 不允许重复值：如果尝试添加一个已经存在的元素，HashSet 会忽略这个操作。
  - 基于哈希表实现：底层使用哈希表（HashMap）来存储数据，因此查找、插入和删除操作的时间复杂度接近 O(1)。

- **适用场景**

  - 当你只需要存储一组**唯一**元素，并且**不关心元素的顺序**时，可以使用 HashSet。
    例如：统计一篇文章中出现的所有单词（每个单词只记录一次）。

  ```java
      HashSet<String> hashSet = new HashSet<>();
      hashSet.add("Apple");
      hashSet.add("Banana");
      hashSet.add("Orange");
      hashSet.add("Apple"); // 尝试添加重复元素
  
      System.out.println(hashSet); // 输出可能是 [Apple, Banana, Orange] 或其他顺序
  ```



#### LinkedHashSet

- 特点

  - 有序： 继承自 HashSet，但通过链表维护了元素的插入顺序。元素的输出顺序与插入顺序一致。
  - 不允许重复值：和 HashSet 一样，不允许存储重复的元素。
  - 基于哈希表 + 链表实现：底层仍然是哈希表，但通过链表记录了元素的插入顺序，因此比 HashSet 稍微慢一点，但仍然很快。

- 适用场景

  - 当你需要存储一组**唯一**元素，并且希望**保持插入顺序**时，可以使用 LinkedHashSet。
    例如：记录用户访问的网页历史（按访问顺序排列）。

  ```java
      LinkedHashSet<String> linkedHashSet = new LinkedHashSet<>();
      linkedHashSet.add("Apple");
      linkedHashSet.add("Banana");
      linkedHashSet.add("Orange");
      linkedHashSet.add("Apple"); // 尝试添加重复元素
  
      System.out.println(linkedHashSet); // 输出一定是 [Apple, Banana, Orange]
  ```



#### **TreeSet**

- 特点

  - 排序：TreeSet 是一个有序集合，对插入的元素进行自然排序（升序），或者根据提供的比较器（Comparator）进行排序。
  - 不允许重复值：不允许存储重复的元素。
  - 基于红黑树实现：底层使用红黑树（一种自平衡二叉搜索树）来存储数据，因此查找、插入和删除操作的时间复杂度为 O(log n)。
    适合范围查询：由于元素是有序的，TreeSet 提供了许多方便的方法，比如获取某个范围内的元素（subSet、headSet、tailSet）。

- 适用场景

  - 当你需要存储一组**唯一**元素，并且希望这些元素**按照某种顺序排列**时，可以使用 TreeSet。
    例如：存储学生成绩并自动按分数排序。

  ```java
      TreeSet<Integer> treeSet = new TreeSet<>();
      treeSet.add(5);
      treeSet.add(2);
      treeSet.add(8);
      treeSet.add(2); // 尝试添加重复元素
  
      System.out.println(treeSet); // 输出一定是 [2, 5, 8]
  
      // 获取小于 5 的所有元素
      System.out.println(treeSet.headSet(5)); // 输出 [2]
  ```