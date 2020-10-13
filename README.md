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

In the above `linearSearch` function the runtime is `O(n)`. Worst case searching a million elements, we would have to iterate through a million elements. 😱

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

In the `binarySearch` function above the runtime is drastically faster as we are using a divide and conquer algorithm and cutting the problem in half on every iteration. Our runtime is logorithmic at `O(logn)` . Worst case searching a million elements, we would have to iterate 20 times, yep 20. 🥳  🤯  Binary search wins...

[Try it here using a log calculator](https://www.rapidtables.com/calc/math/Log_Calculator.html)

## Challenges 

##### Challenge 1 - Convert the binary search solution to be a generic function that works with any type

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

##### Challenge 2 - Binary Search

[LeetCode](https://leetcode.com/problems/binary-search/)

#### Challenge 3 - First bad version 

[LeetCode](https://leetcode.com/problems/first-bad-version/)

## Resources 

1. [Wikipedia - Binary Search](https://en.wikipedia.org/wiki/Binary_search_algorithm)
1. [GeeksForGeeks](https://www.geeksforgeeks.org/binary-search/)
1. [Google AI Blog - bug solved in large array search](https://ai.googleblog.com/2006/06/extra-extra-read-all-about-it-nearly.html)
1. [Log Calculator](https://www.rapidtables.com/calc/math/Log_Calculator.html)
