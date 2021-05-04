# LeetCode 讀書會第 26 次聚會 2021/05/04

  leetcode 讀書會通知
 1. 項目: 第 26 次聚會
 2. 目的: 線上一起寫題目, 由有想法的人帶領, 先解題, 再看該題有趣的解法
 3. 時間: 5/04 (二) 20:00 ~ 21:00
 4. 地點: google meet 線上 (前 10 分鐘預備鏈接)
 5. 解題項目:  [Binary search](https://leetcode.com/explore/learn/card/binary-search)
 6. 共筆: GitHub https://github.com/programmingbookclub/Leetcode-club
 7. 備註: 上次只有聊 658 一個題目，這次會聊  50	 Pow(x, n), 因為 Template analysis 需要付費，但是還是有放在共筆內。

* Template Analysis

* Article Binary Search Template Analysis

* 🔓	 EASY	 270	 Closest Binary Search Tree Value	 https://leetcode.com/problems/closest-binary-search-tree-value

```typescript=
/** 
  嘗試找到 arr[m]，符合 (x - arr[m]) > (arr[m + k] - x)，m 即為解的第一個元素，
  而尋找的過程就可以使用二元搜尋法
  Inspired by [Clean O(logN) solution in Python](https://leetcode.com/explore/learn/card/binary-search/135/template-iii/945/discuss/133604/Clean-O(logN)-solution-in-Python)
  Time Complexity: O( log(n) + k ), Space Complexity: O(k)
  k ==> result's first element in original array's index
  [i ..< i+k] --> 是 result Array
*/
function findClosestElements(arr: number[], k: number, x: number): number[] {
  if (k === arr.length) return arr;
  let left = 0;
  let right = arr.length - k;
  let middle = left + Math.floor((right - left) / 2);
  while(left < right) {
    /** middle 與 x 的差 */
    const middleToX = x - arr[middle];
    /** x 與 middleK 的差，middleK 為 middle + k 的位置 */
    const xToMiddleK = arr[middle + k] - x;

    // arr[middle] 離 x 比較遠，繼續檢查 middle 的右側
    if (middleToX > xToMiddleK) left = middle + 1;
    // arr[middle] 離 x 比較近，繼續檢查 middle 的左側
    else right = middle;
    middle = left + Math.floor((right - left) / 2);
  }
  return arr.slice(middle, middle + k);
};
```

* 🔓	 MEDIUM	 702	 Search in a Sorted Array of Unknown Size	 https://leetcode.com/problems/search-in-a-sorted-array-of-unknown-size

* Conclusion

* MEDIUM	 50	 Pow(x, n)	 https://leetcode.com/problems/powx-n

```typescript
/** Recursion in TS by Louis. It's inspired by [the discussion](https://leetcode.com/explore/learn/card/binary-search/137/conclusion/982/discuss/19546/Short-and-easy-to-understand-solution) */
function myPow(x: number, n: number): number {
  if (n == 0) return 1;
  if (n < 0) return myPow(1 / x, -n);
  if (n % 2 == 0) return myPow(x * x, n / 2);
  else return x * myPow(x * x, Math.floor(n / 2));
};

```typescript
/** Iteration in TS by Louis */
function myPow(x: number, n: number): number {
  let base = x;
  let exponent = n;
  let constant = 1;
  
  if (n === 0) return 1;
  
  if (n < 0) {
    base = 1 / x;
    exponent = -n;
  }
  
  while (exponent > 1) {
    if (exponent % 2 == 0) {
      base = base * base;
      exponent = exponent / 2;
    }
    else {
      constant = constant * base;
      base = base * base;
      exponent = Math.floor(exponent / 2);
    }
  }
  
  return constant * base;
}


* EASY	 367	 Valid Perfect Square	 https://leetcode.com/problems/valid-perfect-square

```typescript
/** Iteration for `Valid Perfect Square` in TS by Louis*/
function isPerfectSquare(num: number): boolean {
  if (num === 1) return true;
  
  let lower = 2;
  let upper = Math.floor(num / 2);
  
  while (lower <= upper) {
    const middle = lower + Math.floor((upper - lower) / 2);
    if (num === middle * middle) return true;
    else if (num > middle * middle) lower = middle + 1;
    else upper = middle - 1;
  }
  return false;
};
```
    // newton method 十分逼近法
  func _newton_isPerfectSquare(_ num: Int) -> Bool {
          var i = num
          while true {
              let p = i * i
              if p <= num {return p == num}
              i = (i + num / i) >> 1
          }
    }
    // newton method 十分逼近法 recursion
      func isPerfectSquare(_ num: Int) -> Bool {
          func helper(_ i: Int) -> Bool { 
             let p = i * i 
              return p <= num ? p == num : helper((i + num / i) >> 1) 
          }
          return helper(num)
    }
    // binary search
    func isPerfectSquare(_ num: Int) -> Bool {
        if num == 1 {return true}
        func helper(_ l: Int, _ u: Int) -> Bool {
            if l >= u {return false}
            let m = (u - l) / 2 + l
            let p = m * m
            if p > num {return helper(l, m)}
            if p < num {return helper(m+1, u)}
            return true
           
        }
        return helper(0, num)
    }
* EASY	 744	 Find Smallest Letter Greater Than Target	 https://leetcode.com/problems/find-smallest-letter-greater-than-target

* More Practices

* MEDIUM	 153	 Find Minimum in Rotated Sorted Array	 https://leetcode.com/problems/find-minimum-in-rotated-sorted-array

* HARD	 154	 Find Minimum in Rotated Sorted Array II	 https://leetcode.com/problems/find-minimum-in-rotated-sorted-array-ii

* EASY	 349	 Intersection of Two Arrays	 https://leetcode.com/problems/intersection-of-two-arrays

* EASY	 350	 Intersection of Two Arrays II	 https://leetcode.com/problems/intersection-of-two-arrays-ii

* EASY	 167	 Two Sum II - Input array is sorted	 https://leetcode.com/problems/two-sum-ii-input-array-is-sorted

* More Practices II

* MEDIUM	 287	 Find the Duplicate Number	 https://leetcode.com/problems/find-the-duplicate-number

* HARD	 4	 Median of Two Sorted Arrays	 https://leetcode.com/problems/median-of-two-sorted-arrays

* HARD	 719	 Find K-th Smallest Pair Distance	 https://leetcode.com/problems/find-k-th-smallest-pair-distance 

* HARD	 410	 Split Array Largest Sum	 https://leetcode.com/problems/split-array-largest-sum
