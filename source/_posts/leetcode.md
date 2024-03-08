---
title: LeetCode
date: 2024-02-27 09:51:44
background: bg-[#2a338a]
tags:
categories:
  - Programming
intro: |
    记录力扣关键算法代码片段及找工作记录
plugins:
  - copyCode
---

复杂度分析
----


### 什么是大O

- 大O用来表示上界的，作为算法的最坏情况运行时间的上界
- 面试中说道算法的时间复杂度是多少指的都是一般情况，而不是严格的上界
- 大O就是数据量级突破一个点且数据量级非常大的情况下所表现出的时间复杂度


排序
----




数组
----

### 二分查找

- 注意区间定义，[left, right] or [left, right)
- 若右边是闭区间，`right = len - 1`，判断为 `left <= right`

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        left, right = 0, len(nums)-1
        while left<=right:
            mid = (right - left)//2 + left # 防止溢出 等同于(left + right)//2
            if nums[mid] > target:
                right = mid - 1
            elif nums[mid] < target:
                left = mid + 1
            elif nums[mid] == target:
                return mid
        return -1
```

- 插入的问题最后改为 `return right + 1`
- 平方根问题：$k^2 < x$，找到 k


### 移除元素
双向指针方法

- 首尾指针，会改变元素相对位置
```python
while nums[len_nums - rm_num - 1] == val and len_nums - rm_num - 1 > i:
    rm_num += 1
```

- 快慢指针，元素相对位置不变
```python
while fast < size:  
    if nums[fast] != val:
        nums[slow] = nums[fast]
        slow += 1
    fast += 1
```

### 有序数组平方
- 首尾双指针，先定义列表，然后就可以升降序
```python
l, r, i = 0, len(nums)-1, len(nums)-1
res = [float('inf')] * len(nums) # 需要提前定义列表，存放结果
```

### 螺旋矩阵
- 定义矩阵 `matrix = [[0] * n for _ in range(n)]`
- 先计算要转多少圈 `loop_time = n//2+n%2`
- 然后每个圈 四次硬for循环就好



投递岗位
----


### 美团
投递记录： [美团](https://zhaopin.meituan.com/web/position/detail?jobUnionId=2309322580&jobShareType=1&highlightType=campus)
- 志愿一：【转正实习】自动驾驶算法工程师
- 志愿二：【转正实习】无人配送/机器人算法工程师
- 志愿三：【转正实习】计算机视觉工程师


### 小米
投递记录： [小米](https://xiaomi.jobs.f.mioffice.cn/internship/?spread=6AA3R7B)
- TODO 【BEVDet，BEVFusion，Occupancy Network】

考虑：
- [自动驾驶感知算法实习生](https://xiaomi.jobs.f.mioffice.cn/internship/position/7224347784110997613/detail?spread=6AA3R7B)
- [自动驾驶感知算法实习生—上海](https://xiaomi.jobs.f.mioffice.cn/internship/position/7267745116868444268/detail?spread=6AA3R7B)

### 腾讯
投递记录： [腾讯](https://mp.weixin.qq.com/s/0Pz2KLy68dn7uh3FJ5Ox2g)
- TODO


### 大疆
投递记录：[大疆](https://we.dji.com/zh-CN/position/detail?positionId=1666282101300531200)
- TODO

考虑：
- [高级计算机视觉算法工程师（无人机）](https://we.dji.com/zh-CN/position/detail?positionId=1666282101300531200)
