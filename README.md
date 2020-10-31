# Binary-Search

Binary Search in Swift. 

> Wikipedia: In computer science, binary search, also known as half-interval search, logarithmic search, or binary chop, is a search algorithm that finds the position of a target value within a sorted array. Binary search algorithm runtime of `O(log n)` has a more optimal runtime as opposed to linear search `O(n)`. 

![big O cheatsheet](https://camo.githubusercontent.com/99bb7ce9057401d1ea21a98e907c9dffe40daf74/68747470733a2f2f6d69726f2e6d656469756d2e636f6d2f6d61782f313230302f312a5f6e734d5645456b49723143483861486a544e627a412e6a706567)

## 1. Linear Search 

```swift 
func linearSearch(_ arr: [Int], _ target: Int) -> Int {
  for (index, num) in arr.enumerated() { // for loop runs O(n) times e.g 15 times if 16 elements and target is last
    if num == target {
      return index
    }
  }
  return -1
}

linearSearch([1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16], 16) // index 15 returned
```

In the above `linearSearch` function the runtime is `O(n)`. Worst case searching a million elements, we would have to iterate through a million elements. 😱

## 2. Binary Search 

![binary search sketch](https://user-images.githubusercontent.com/1819208/95866495-fc2a7200-0d35-11eb-9c03-23cadc22d0a4.jpg)

```swift 
func binarySearch(_ arr: [Int], _ target: Int) -> Int {
  var low = 0
  var high = arr.count
  while low < high { // while loop runs O(log n) times e.g will be 4 times, worst case target is the last of 16 elements
    let middleIndex = low + (high - low) / 2
    if arr[middleIndex] == target {
      return middleIndex
    } else if arr[middleIndex] > target { // go left
      high = middleIndex
    } else { // go right
      low = middleIndex + 1
    }
  }
  return -1
}

binarySearch([1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16], 16) // index 15 returned
```

In the `binarySearch` function above the runtime is drastically faster as we are using a divide and conquer algorithm and cutting the problem in half on every iteration. Our runtime is logorithmic at `O(logn)` . Worst case searching a million elements, we would have to iterate 20 times, yep 20. 🥳  🤯  Binary search wins...linear would be 1 million times in the worst case scenario that the target element is last in the collection.

[Try it here using a log calculator](https://www.rapidtables.com/calc/math/Log_Calculator.html)

## Challenges 

#### Challenge 1 - Convert the binary search solution to be a generic function that works with any type

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

#### Challenge 2 - Binary Search

[LeetCode](https://leetcode.com/problems/binary-search/)

#### Challenge 3 - First bad version 

[LeetCode](https://leetcode.com/problems/first-bad-version/)

#### Challenge 4 - Write binary search using recursion 

Write binary search using recursion

## Resources 

1. [Wikipedia - Binary Search](https://en.wikipedia.org/wiki/Binary_search_algorithm)
1. [GeeksForGeeks](https://www.geeksforgeeks.org/binary-search/)
1. [Google AI Blog - bug solved in large array search](https://ai.googleblog.com/2006/06/extra-extra-read-all-about-it-nearly.html)
1. [Log Calculator](https://www.rapidtables.com/calc/math/Log_Calculator.html)
