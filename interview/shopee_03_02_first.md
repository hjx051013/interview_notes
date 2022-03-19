# shopee一面记录

1. 2*n长度的数组，划分成长度相等的两个子数组，使两数组和相差最小
```
class Solution:
    def __init__(self):
        self.res1 = float('inf')
        self.res2 = float('inf')
        self.arr = None
        self.sum = None

    def splitArray(self, arr):
        self.arr = arr
        self.sum = sum(arr)
        self.dfs(0, 0, 0)
        return self.res2
    
    def dfs(self, index, preNum, preSum):
        if preSum-(self.sum-preSum) > self.res2:
            return
        if len(self.arr)-index+preNum < len(self.arr)//2:
            return
        if preNum == len(self.arr)//2:
            if self.res1 > abs(self.sum//2-preSum):
                self.res1 = abs(self.sum//2-preSum)
                self.res2 = abs(self.sum-preSum-preSum)
            return
        # select
        self.dfs(index+1, preNum+1, preSum+self.arr[index])
        
        self.dfs(index+1, preNum, preSum)

if __name__ == "__main__":
    sol = Solution()
    print(sol.splitArray([1,2,3,4,5,6]))
```

2. mysql的索引底层数据结构
- memory引擎支持哈希索引。 不需要排序、范围查询的需求，只需要做等值比较查询。
- innodb存储引擎和MyISAM存储引擎支持B+树索引
    - 

3. 讲讲mysql的隔离级别，默认隔离级别是什么？

4. 生产过程中有修改过隔离级别的吗？

5. 可重复读隔离级别的实现机制？

6. redis的哨兵是干什么的？

7. 数据结构中小顶堆插入元素的过程

8. 熟悉Gin吗？

9. TCP如何保持保证可靠性？
- 序列号和确认应答信号。通过序列号和确认应答信号确保了数据不会重复发送和重复接收
- 超时重发控制
- 连接管理
- 滑动窗口控制
- 流量控制
- 拥塞控制

10. TCP拥塞控制算法？
