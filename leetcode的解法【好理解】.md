# leetcode239. 滑动窗口最大值：给一个整数数组 nums，有一个大小为 k 的滑动窗口从数组的最左侧移动到数组的最右侧。只可以看到在滑动窗口内的 k 个数字。滑动窗口每次只向右移动一位。返回：滑动窗口中的最大值。

```python
class Solution:
    def maxSlidingWindow(self, nums, k):
        q = deque()
        res = []
        for i, num in enumerate(nums):
            if q and i - k == q[0]:
                q.popleft()
            while q and num >= nums[q[-1]]:
                q.pop()
            q.append(i)
            if i >= k - 1:
                res.append(nums[q[0]])
        return res
```

## 有点两数之和的味道，这个好理解一些。
