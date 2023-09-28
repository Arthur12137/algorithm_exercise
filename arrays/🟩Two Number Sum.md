# Two Number Sum

Given an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_.

You may assume that each input would have **_exactly_ one solution**, and you may not use the _same_ element twice.

You can return the answer in any order.

**Example 1:**

**Input:** nums = [2,7,11,15], target = 9
**Output:** [2,9]

**Example 2:**

**Input:** nums = [3,2,4], target = 6
**Output:** [2,4]

## First Solution 
`Time Complexity`:   O(n^2)
`Spece Complexity`: O(1)
The solution leverages a classic nested iteration methodology. Using an outer loop, we iterate over each element as a primary anchor point. The inner loop, for each anchor, traverses the succeeding elements to identify potential pairs. By systematically evaluating each pair against our target sum using this O(n^2) approach, we can pinpoint and return the requisite combination efficiently. 
```Python
def twoNumberSum(array, targetSum):
	for i in range(len(array)-1):
		firstNum = array[i]
		for j in range(i+1, len(array)):
			secondNum = array[j]
			if firstNum + SecondNum = targetSum:
				return [firstNum, secondNum]
```



## Second Solution
`Time Complexity`: O(n)
`Spece Complexity`: O(n)
The `twoNumberSum` function takes an array of numbers and a target sum as its parameters. It aims to find two distinct numbers in the array that add up to the target sum. The function employs a dictionary, `nums`, to store numbers from the array as it iterates through them. For each number in the array, the function calculates the complementary value needed to reach the target sum. If this complementary value is already in the `nums` dictionary, it means we've found the two numbers that add up to the target sum and they are returned as a pair. If no such pair is found by the end of the iteration, the function returns an empty list.

```Python
def twoNumberSum(array, targetSum):
	nums = {}
	for num in array:
		potentialMatch = targetSum - num
		if potentialMatch in nums:
			return [potentialMatch, num]
		else:
			nums[num] = True
	return []
```



## Third Solution
`Time Complexity`: O(nlog(n))
`Spece Complexity`: O(1)
The third solution is an optimized method. To optimize the search:

1. The function first sorts the array.
2. It then uses a two-pointer approach. One pointer (`left`) starts at the beginning of the array, and the other (`right`) starts at the end.
3. In a loop, it calculates the sum of the numbers at the current positions of these pointers.
4. If this sum equals the target, the function returns the two numbers.
5. If the sum is less than the target, it moves the `left` pointer one step to the right to increase the sum.
6. If the sum is greater than the target, it moves the `right` pointer one step to the left to decrease the sum.
7. This continues until the two pointers meet. If no pair of numbers is found that matches the target sum, the function returns an empty list.

Note: There's a small typo in your function. The line `if currentSum = targetSum:` should be `if currentSum == targetSum:`.
```Python
def twoNumberSum(array, targetSum):
	array.sort()
	left = 0
	right = len(array) - 1
	while left < right:
		currentSum = array[left] + array[right]
		if currentSum == targetSum:
			return [array[left], array[right]]
		elif currentSum < targetSum:
			left += 1
		elif currentSum > targetSum:
			right -= 1
	return []
```