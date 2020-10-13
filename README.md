# Binary-Search

Binary Search in Swift. 

> Wikipedia: In computer science, binary search, also known as half-interval search, logarithmic search, or binary chop, is a search algorithm that finds the position of a target value within a sorted array

## 1. Linear Search 

```swift 
func linearSearch(_ nums: [Int], _ target: Int) -> Int {
  for (index, num) in nums.enumerated() { // O(n)
    if num == target {
      return index
    }
  }
  return -1
}

linearSearch([-6, 2, 5, 9, 11, 45, 78], 2) // index 1 returned
```

## 2. Binary Search 

```swift 
func binarySearch(_ nums: [Int], _ target: Int) -> Int {
  var low = 0
  var high = nums.count
  
  while low < high {
    let middleIndex = low + (high - low) / 2 // divide in half each time => O(log n)
    if nums[middleIndex] == target {
      return middleIndex
    } else if nums[middleIndex] > target { // look left
      high = middleIndex
    } else { // look right
      low = middleIndex + 1
    }
  }
  return -1
}

binarySearch([-6, 2, 5, 9, 11, 45, 78], 2) // index 1 returned
```

## Challenges 

##### Challenge 1 - Binary Search

[LeetCode - binary search](https://leetcode.com/problems/binary-search/)

#### Challenge 2 - First bad version 

[LeetCode](https://leetcode.com/problems/first-bad-version/)

## Resources 

1. [Wikipedia - Binary Search](https://en.wikipedia.org/wiki/Binary_search_algorithm)
1. [GeeksForGeeks](https://www.geeksforgeeks.org/binary-search/)
