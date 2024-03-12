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

### Git

```bash
# Add a git URL as an alias
git remote add [alias] [url] 
```

```bash
# Change the URL of the git repo
git remote set-url origin [git_url] 
```

### Git Merge

```bash
# 更新所有远程分支
git remote update

# 拉取远程仓库到本地新建branch
git fetch <远程主机名>(origin) <远程分支名>:<本地新分支名>

# 复制当前分支到一个新的分支，并且会切换过去
git checkout -b 新分支名

# 复制当前分支到一个新的分支，并且会切换过去
git merge <本地新分支名> 
```
然后根据提示解决[问题冲突](https://juejin.cn/post/7004643157279244325)，再之后push即可



Deep Learning 
---------------

### 卷积神经网络

- [计算机视觉面试题-网络结构相关问题总结](https://zhuanlan.zhihu.com/p/556521788)
    - 使用3个 3x3conv 而不 7x7conv 是可以降低计算量
- [卷积核的数量决定了输出特征的维度（通道数）](https://blog.csdn.net/weixin_42863507/article/details/106320968)
- 输入特征的维度决定了每个卷积核的通道数
    - 即每个卷积核是有通道数的概念的

### ResNet

- 深度网络能够合并不同层次的特征信息
- 阻碍收敛的梯度消失/爆炸
    - normalized initialization and intermediate normalization layer 可以解决问题
- ResNet解决的是Deep Net 深度增加时的退化问题
- Bottleneck 在增加深度的同时不会额外增加参数量



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