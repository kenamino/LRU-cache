<div align="center">

# LRU Cache

![Language](https://img.shields.io/badge/Language-C/C++-blue?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)

> **LRU (Least Recently Used) 缓存实现** — O(1) 时间复杂度的get/put操作

</div>

---

## 简介

LRU (Least Recently Used) 是一种常见的缓存淘汰策略。当缓存容量满时，优先移除最近最少使用的数据。

本项目使用 **哈希表 + 双向链表** 实现 O(1) 时间复杂度的 `get` 和 `put` 操作。

## 核心数据结构

```
Hash Map                Doubly Linked List
┌─────────┐            ┌───┐    ┌───┐    ┌───┐    ┌───┐
│ key: 1 ─┼───────────►│ 1 │◄──►│ 2 │◄──►│ 3 │◄──►│ 4 │
│ key: 2 ─┼───────────►│   │    │   │    │   │    │   │
│ key: 3 ─┼───────────►└───┘    └───┘    └───┘    └───┘
│ key: 4 ─┼───────────►  MRU ◄─────────────────► LRU
└─────────┘           (最近使用)            (最久未使用)
```

## API 接口

| 方法 | 说明 | 时间复杂度 |
|:---|:---|:---:|
| `get(key)` | 获取 key 对应的值，不存在返回 -1 | O(1) |
| `put(key, value)` | 插入/更新键值对，满时淘汰最久未使用 | O(1) |

## 使用示例

```
LRUCache cache = new LRUCache(2);  // 容量为 2

cache.put(1, 1);
cache.put(2, 2);
cache.get(1);      // 返回 1
cache.put(3, 3);   // 淘汰 key=2
cache.get(2);      // 返回 -1 (未找到)
cache.put(4, 4);   // 淘汰 key=1
cache.get(1);      // 返回 -1 (未找到)
cache.get(3);      // 返回 3
cache.get(4);      // 返回 4
```

## 编译运行

```bash
# C 版本
gcc lru_cache.c -o lru_cache
./lru_cache

# C++ 版本
g++ -std=c++17 lru_cache.cpp -o lru_cache
./lru_cache
```

## 复杂度分析

| 操作 | 时间复杂度 | 空间复杂度 |
|:---|:---:|:---:|
| get | O(1) | O(n) |
| put | O(1) | O(n) |

> n 为缓存容量

---

## 许可证

[MIT License](./LICENSE)

---

<div align="center">

*Created by [kenamino](https://github.com/kenamino)*

</div>
