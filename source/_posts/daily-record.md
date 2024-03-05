---
title: Daily-Record
date: 2024-03-01 18:41:20
background: bg-[#436b97]
tags:
    - script
    - interpret
categories:
    - Programming
intro: |
    记录我平时遇到的解决各种问题的代码片段
plugins:
    - copyCode
---

Linux
---------------


### Unzip

```bash
unzip -O UTF-8 your_zip_file.zip
```
- [Link](https://quickref.me/quickref)

解决解码时中文乱码的问题

### 统计文件数量

```bash
# 统计当前目录下文件的个数（不包括目录
ls -l | grep "^-" | wc -l

# 统计当前目录下文件的个数（包括子目录
ls -lR| grep "^-" | wc -l

# 查看某目录下文件夹的个数（包括子目录
ls -lR | grep "^d" | wc -l
```



Python
---------------


### Multi-Process {.col-span-2 .row-span-3}

```python
import multiprocessing

manager = multiprocessing.Manager()
# output = manager.list() # 可用于多线程的全局变量
# num_sum = manager.Value(int, 0)  # num_sum.value
# lock = manager.Lock()  # with lock: 用于防止冲突
total_len = len(data_list)
process_num = 20 # 使用多少个线程并行处理
tmp_len = total_len // process_num + 1
q = multiprocessing.Queue()
jobs = []
for i in range(process_num):
    data_list_temp = data_list[tmp_len * i : min(tmp_len * (i + 1), total_len)]
    p = multiprocessing.Process(target=Process_fun, args=(args0, ))
    jobs.append(p)
    p.start()
    
for p in jobs:
    p.join()

```