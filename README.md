# Algorithms-and-datastructures-Leetcode

Решения задач по алгоритмам и структурам данных с LeetCode и Hackerrank на Python.

## 509. Fibonacci Number

![509. Fibonacci Number](images/509.%20Fibonacci%20Number.png)

```Python
class Solution:
    def fib(self, n: int) -> int:
        f0 = 0
        f1 = 1
        if n == 0: return f0
        if n == 1: return f1
        for i in range(0,n-1):
            fn = f1 + f0
            f0 = f1
            f1 = fn
        return fn
```

## 70. Climbing Stairs

![70. Climbing Stairs](images/70.%20Climbing%20Stairs.png)

```Python
class Solution:
    def climbStairs(self, n: int) -> int:
        if n == 1: return 1
        f1 = 1
        f2 = 1
        for i in range(0,n-1):
            f3 = f2 + f1
            f1 = f2
            f2 = f3
        return f3
```

## 75. Sort Colors

![75. Sort Colors](images/75.%20Sort%20Colors.png)

```Python
class Solution:
    def sortColors(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        low = mid = 0
        high = len(nums) - 1
        while mid <= high:
            if nums[mid] == 0:
                nums[low], nums[mid] = nums[mid], nums[low]
                low += 1
                mid += 1
            elif nums[mid] == 1:
                mid += 1
            else:
                nums[mid], nums[high] = nums[high], nums[mid]
                high -= 1
```

## Counting Sort 1

![Counting Sort 1](images/Counting%20Sort%201.png)

```Python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'countingSort' function below.
#
# The function is expected to return an INTEGER_ARRAY.
# The function accepts INTEGER_ARRAY arr as parameter.
#

def countingSort(arr):
    result = [0] * 100
    for i in range(len(arr)):
        result[arr[i]] +=1
    return result

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')

    n = int(input().strip())

    arr = list(map(int, input().rstrip().split()))

    result = countingSort(arr)

    fptr.write(' '.join(map(str, result)))
    fptr.write('\n')

    fptr.close()
```

## Counting Sort 2

![Counting Sort 2](images/Counting%20Sort%202.png)

```Python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'countingSort' function below.
#
# The function is expected to return an INTEGER_ARRAY.
# The function accepts INTEGER_ARRAY arr as parameter.
#

def countingSort(arr):
    min_value = min(arr)
    counts = [0] * 100

    for value in arr:
        counts[value - min_value] += 1

    result: list[int] = []
    for index, count in enumerate(counts):
        result.extend([index + min_value] * count)
    return result

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')

    n = int(input().strip())

    arr = list(map(int, input().rstrip().split()))

    result = countingSort(arr)

    fptr.write(' '.join(map(str, result)))
    fptr.write('\n')

    fptr.close()
```

## Counting Sort 3

![Counting Sort 3](images/Counting%20Sort%203.png)

```Python
n = int(input())
result = [0] * 100

for i in range(n):
    x, y = map(str, input().split())
    result[int(x)] += 1

total = 0
output = []
for i in range(len(result)):
    total += result[i]
    output.append(str(total))

print(" ".join(output))
```

## Quicksort 1 - Partition

![Quicksort 1 - Partition](images/Quicksort%201%20-%20Partition.png)

```Python
#!/bin/python3

import math
import os
import random
import re
import sys

#
# Complete the 'quickSort' function below.
#
# The function is expected to return an INTEGER_ARRAY.
# The function accepts INTEGER_ARRAY arr as parameter.
#

def quickSort(arr):
    pivot = arr[0]
    left = [x for x in arr if x < pivot]
    equal = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    return left + equal + right
    
    
if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')

    n = int(input().strip())

    arr = list(map(int, input().rstrip().split()))

    result = quickSort(arr)

    fptr.write(' '.join(map(str, result)))
    fptr.write('\n')

    fptr.close()
```

## 347. Top K Frequent Elements

![347. Top K Frequent Elements](images/347.%20Top%20K%20Frequent%20Elements.png)

```Python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        counter = {}
        for num in nums:
            if num not in counter:
                counter[num] = 1
            else:
                counter[num] += 1
        counter = dict(sorted(counter.items(), key=lambda x: x[1], reverse=True))
        result = list(counter.keys())[:k]
        return result
```

## 215. Kth Largest Element in an Array

![215. Kth Largest Element in an Array](images/215.%20Kth%20Largest%20Element%20in%20an%20Array.png)

```Python
class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        mn = min(nums)
        mx = max(nums)

        buckets = [[] for bucket in range(mx - mn + 1)]

        for num in nums:
            buckets[num - mn].append(num)

        count = 0
        for i in range(len(buckets) - 1, -1, -1):
            if buckets[i]:
                count += len(buckets[i])
                if count >= k:
                    return buckets[i][0]
```

## 20. Valid Parentheses

![20. Valid Parentheses](images/20.%20Valid%20Parentheses.png)

```Python
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        for char in s:
            if char == ')' and stack and stack[-1] == '(':
                stack.pop()
            elif char == ']' and stack and stack[-1] == '[':
                stack.pop()
            elif char == '}' and stack and stack[-1] == '{':
                stack.pop()
            else:
                stack.append(char)
        return not stack
```

## 225. Implement Stack using Queues

![225. Implement Stack using Queues](images/225.%20Implement%20Stack%20using%20Queues.png)

```Python
class MyStack:

    def __init__(self):
        self.queue = deque()

    def push(self, x: int) -> None:
        self.queue.append(x)
        for i in range(len(self.queue) - 1):
            self.queue.append(self.queue.popleft())

    def pop(self) -> int:
        if self.empty():
            return -1
        return self.queue.popleft()

    def top(self) -> int:
        if self.empty():
            return -1
        return self.queue[0]

    def empty(self) -> bool:
        return len(self.queue) == 0
```

## 232. Implement Queue using Stacks

![232. Implement Queue using Stacks](images/232.%20Implement%20Queue%20using%20Stacks.png)

```Python
class MyQueue:

    def __init__(self):
        self.in_stack = []
        self.out_stack = []

    def push(self, x: int) -> None:
        self.in_stack.append(x)

    def pop(self) -> int:
        if not self.out_stack:
            while self.in_stack:
                self.out_stack.append(self.in_stack.pop())
        return self.out_stack.pop()

    def peek(self) -> int:
        if not self.out_stack:
            while self.in_stack:
                self.out_stack.append(self.in_stack.pop())
        return self.out_stack[-1]

    def empty(self) -> bool:
        return not self.in_stack and not self.out_stack
```
