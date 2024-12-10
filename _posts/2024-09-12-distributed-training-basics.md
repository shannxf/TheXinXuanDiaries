---
layout: post
author: Xuan Feng
tags: [distributed training, computer architecture]
---
## 分布式训练：通信

### 1. broadcast

一个节点（root/master）发送同样的数据给其他所有节点

- 应用场景
- 举例

### 2. scatter

### 3. reduce

### 4. all-reduce

### 5. gather

### 6. all-gather



## 分布式训练：并行方法

### 1. 数据并行

每个节点有相同的模型参数，和一部分输入数据

参数更新的同步很重要

### 2. 张量并行

### 3. 流水线并行

### 4. 