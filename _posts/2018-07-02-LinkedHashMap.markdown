---
layout: post
title:  "LinkedHashMap的使用场景"
date:   2018-07-03 20:00:00 +0800
categories: Java基础 数据结构
---
### 描述
LinkedHashMap是HashMap的子类。LinkedHashMap是有序的，而HashMap是无序的。
从数据结构来看，在HashMap的基础上，增加双向链表的结构，即每一个节点增加before，after属性。
```java
/**
 * HashMap.Node subclass for normal LinkedHashMap entries.
 */
static class Entry<K,V> extends HashMap.Node<K,V> {
    Entry<K,V> before, after;
    Entry(int hash, K key, V value, Node<K,V> next) {
        super(hash, key, value, next);
    }
}
```
从性能上来看，由于增加了维护链表的开支，其性能可能比HashMap稍逊一筹。LinkedHashMap的迭代速度和映射的大小成正比，即O(n)，而HashMap的迭代很可能比较大，HashMap的迭代所需时间和容量成正比。
### 特性
### 使用场景
#### 按使用顺序排序
如果模块通过输入得到一个映射，复制这个映射，然后返回由此副本确定其顺序的结果，这种情况下这项技术特别有用。（客户通常期望返回的内容与其出现的顺序相同。）
#### LRUCache
提供特殊的构造方法来创建链接哈希映射，该哈希映射的迭代顺序就是最后访问其条目的顺序，从近期访问最少到近期访问最多的顺序（访问顺序）。这种映射很适合构建 LRU 缓存。   
ehcache的LRUCache就是基于LinkedHashMap改造的。
