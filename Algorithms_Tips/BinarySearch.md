# Binary Search Template:
各类型总结
https://leetcode-cn.com/problems/find-first-and-last-position-of-element-in-sorted-array/solution/yi-ge-mo-ban-tong-sha-suo-you-er-fen-cha-zhao-wen-/
```
//查找指定值的位置
func searchInsert(nums []int, target int) int {
    left, right := 0, len(nums)-1
    for left <= right {
        mid := left + (right-left) >> 1
+       if nums[mid] == target {
+           return mid
+       }
        if nums[mid] > target { // 这里用 > 就可以了，上面已经判断过 =
            right = mid - 1
        } else {
            left = mid + 1
        }
    }
    return left
}

// 查找满足 x ≥ target 的下界的下标
func LowerBound(nums []int, target int) int {
    left, right := 0, len(nums)-1
    for left <= right {
        mid := left + (right-left) >> 1
        if nums[mid] >= target { // 这里的比较运算符与题目要求一致
            right = mid - 1
        } else {
            left = mid + 1
        }
    }
    return left // 返回下界的下标
}

// 查找满足 x > target 的下界的下标
func LowerBound(nums []int, target int) int {
    left, right := 0, len(nums)-1
    for left <= right {
        mid := left + (right-left) >> 1
        if nums[mid] > target { // 这里的比较运算符与题目要求一致
            right = mid - 1
        } else {
            left = mid + 1
        }
    }
    return left // 返回下界的下标
}

// 查找满足 x ≤ target 的上界的下标
func LowerBound(nums []int, target int) int {
    left, right := 0, len(nums)-1
    for left <= right {
        mid := left + (right-left) >> 1
        if nums[mid] >= target { // 这里的比较运算符与题目要求一致
            right = mid - 1
        } else {
            left = mid + 1
        }
    }
    return left - 1 // 返回下界的下标
}

// 查找满足 x < target 的下界的下标
func LowerBound(nums []int, target int) int {
    left, right := 0, len(nums)-1
    for left <= right {
        mid := left + (right-left) >> 1
        if nums[mid] >= target { // 这里的比较运算符与题目要求一致
            right = mid - 1
        } else {
            left = mid + 1
        }
    }
    return left - 1 // 返回下界的下标
}

//查找指定值第一次出现的位置
查找满足 x == target 的第一个元素，如果不存在，返回 -1。
只需要先查找满足 x >= target 的下界，然后再判断下界与 target 是否相等。只需在模板代码中增加一个判断：
func searchFirst(nums []int, target int) int {
    left, right := 0, len(nums)-1
    for left <= right {
        mid := left + (right-left) >> 1
        if nums[mid] >= target {
            right = mid - 1
        } else {
            left = mid + 1
        }
    }
+   if left >= len(nums) || nums[left] != target { // 判断一下是否越界，或者不相等
+       return -1
+   }
    return left
}

//查找指定值最后一次出现的位置
查找满足 x == target 的最后一个元素，如果不存在，返回 -1。
只需要先查找满足 x <= target 的上界，然后再判断上界与 target 是否相等。上文中已经描述了如何将查找上界转化为查找下界，直接调用模板代码：
func searchLast(nums []int, target int) int {
    left, right := 0, len(nums)-1
    for left <= right {
        mid := left + (right-left) >> 1
        if nums[mid] > target { // 这里是 > 而不是 >=
            right = mid - 1
        } else {
            left = mid + 1
        }
    }
    if right < 0 || nums[right] != target { // 判断一下是否越界，或者不相等
        return -1
    }
    return right // 这里返回 right 而不是 left
}

```
  

