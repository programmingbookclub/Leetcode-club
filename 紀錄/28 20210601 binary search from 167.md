# LeetCode 讀書會第 28 次聚會 2021/06/01

## leetcode 讀書會通知

1. 項目: 第 28 次聚會
2. 目的: 線上一起寫題目, 由有想法的人帶領, 先解題, 再看該題有趣的解法
3. 時間: 06/01 (二) 20:00 ~ 21:00
4. 地點: google meet 線上 (前 10 分鐘預備鏈接)
5. 解題項目:  [Binary search](https://leetcode.com/explore/learn/card/binary-search)
6. 共筆: GitHub https://github.com/programmingbookclub/Leetcode-club
7. 備註: 這次的進度為 More Practices - No. 167 開始。

* More Practices

* EASY	 167	 Two Sum II - Input array is sorted	 https://leetcode.com/problems/two-sum-ii-input-array-is-sorted

Solution 1 : Two point
```text
l = 0 , r = numbers.count
while l < r 
if L + R = target --> answer
if L + R < target --> l += 1 
if L + R > target --> r -= 1
 
Solution 2 : Binary search
for i in 0..<number.count {
  let t = target - snumber[i]
  binarySearch t in number i+1 ..< count
}
```

* More Practices II

* MEDIUM	 287	 Find the Duplicate Number	 https://leetcode.com/problems/find-the-duplicate-number
```text
     m
     2    
[1,3,4,2,2]
count = 3
3~4 -> 3 
l,u
1 4 => m = 2 , c = 3 ->(1,m=2)
1 2 => m = 1 , c = 1 -> (1+1, 2)
2 2 ==> return l=2

0~count
1~count-1
1~n+1 --> n+1/2
k == count ok part search high
k == count NG part search low
```

```swift
// Binary Search 
func binary_findDuplicate(_ nums: [Int]) -> Int {
    let n+1 = nums.count
    var (l, u) = (1, nums.count - 1)
    while true {
        guard l < u else { return l}
        let m = l + (u - l) >> 1
        var count = 0
        for i in nums{
            if i <= m {count += 1}
        }
        if count <= m {l = m + 1}
        else {u = m}
    }
}
```

Fast slow pointer
> The main idea is the same with problem Linked List Cycle II,https://leetcode.com/problems/linked-list-cycle-ii/. Use two pointers the fast and the slow. The **fast** one goes forward two steps each time, while the **slow** one goes only step each time. They must meet the same item when slow==fast. In fact, they meet in a circle, the duplicate number must be the entry point of the circle when visiting the array from nums[0]. Next we just need to find the entry point. We use a point(we can use the fast one before) to visit form begining with one step each time, do the same job to slow. When fast==slow, they meet at the entry point of the circle. The easy understood code is as follows.
> https://leetcode.com/problems/find-the-duplicate-number/discuss/72846/My-easy-understood-solution-with-O(n)-time-and-O(1)-space-without-modifying-the-array.-With-clear-explanation.
```swift
// Two pointer (fast+slow)
func fastslow_findDuplicate(_ nums: [Int]) -> Int {
    var (slow, fast) = (nums[0], nums[nums[0]])
    while true {
        if slow == fast {break}
        (slow, fast) = (nums[slow], nums[nums[fast]])
    }
    fast = 0
    while true {
        if fast == slow {return slow}
        (slow, fast) = (nums[slow], nums[fast])
    }
}
```

* HARD	 4	 Median of Two Sorted Arrays	 https://leetcode.com/problems/median-of-two-sorted-arrays

* HARD	 719	 Find K-th Smallest Pair Distance	 https://leetcode.com/problems/find-k-th-smallest-pair-distance 

* HARD	 410	 Split Array Largest Sum	 https://leetcode.com/problems/split-array-largest-sum
