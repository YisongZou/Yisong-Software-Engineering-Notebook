# Binary Search Template:
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
  
## Recursive
 ```
 // C++ program to implement recursive Binary Search 
#include <bits/stdc++.h> 
using namespace std; 
  
// A recursive binary search function. It returns 
// location of x in given array arr[l..r] is present, 
// otherwise -1 
int binarySearch(int arr[], int l, int r, int x) 
{ 
    if (r >= l) { 
        int mid = l + (r - l) / 2; 
  
        // If the element is present at the middle 
        // itself 
        if (arr[mid] == x) 
            return mid; 
  
        // If element is smaller than mid, then 
        // it can only be present in left subarray 
        if (arr[mid] > x) 
            return binarySearch(arr, l, mid - 1, x); 
  
        // Else the element can only be present 
        // in right subarray 
        return binarySearch(arr, mid + 1, r, x); 
    } 
  
    // We reach here when element is not 
    // present in array 
    return -1; 
} 
  
int main(void) 
{ 
    int arr[] = { 2, 3, 4, 10, 40 }; 
    int x = 10; 
    int n = sizeof(arr) / sizeof(arr[0]); 
    int result = binarySearch(arr, 0, n - 1, x); 
    (result == -1) ? cout << "Element is not present in array"
                   : cout << "Element is present at index " << result; 
    return 0; 
} 
 ```
## Iterative 
 ```
 // C++ program to implement iterative Binary Search 
#include <bits/stdc++.h> 
using namespace std; 
  
// A iterative binary search function. It returns 
// location of x in given array arr[l..r] if present, 
// otherwise -1 
int binarySearch(int arr[], int l, int r, int x) 
{ 
    while (l <= r) { 
        int m = l + (r - l) / 2; 
  
        // Check if x is present at mid 
        if (arr[m] == x) 
            return m; 
  
        // If x greater, ignore left half 
        if (arr[m] < x) 
            l = m + 1; 
  
        // If x is smaller, ignore right half 
        else
            r = m - 1; 
    } 
  
    // if we reach here, then element was 
    // not present 
    return -1; 
} 
  
int main(void) 
{ 
    int arr[] = { 2, 3, 4, 10, 40 }; 
    int x = 10; 
    int n = sizeof(arr) / sizeof(arr[0]); 
    int result = binarySearch(arr, 0, n - 1, x); 
    (result == -1) ? cout << "Element is not present in array"
                   : cout << "Element is present at index " << result; 
    return 0; 
} 

 ```
