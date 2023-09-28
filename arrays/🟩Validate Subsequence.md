# Validate Subsequence

## Question Description

Given two non-empty arrays of integers, write a function that determines whether the second array is a subsequence of the first one. 

A subsequence of an array is a set of numbers that aren't necessarily adjacent in the array but that are in the same order as they appear in the array. For instance, the number `[1,3,4]` form a subsequence of the array `[1,2,3,4]`, and so do the numbers `[2,4]`. Note that a single number in an array and the array itself are both valid subsequences of the array. 



## Solution 1 
The `isValidSubsequence` function checks if a given `sequence` can be formed as a subsequence from an `array`. The function employs a two-pointer technique:

1. Two pointers, `arrIdx` and `seqIdx`, are initialized to 0. They traverse through the `array` and `sequence` respectively.
2. The main loop continues as long as both pointers are within their respective array/sequence boundaries.
3. Inside the loop, if the current element of the `array` (pointed by `arrIdx`) matches the current element of the `sequence` (pointed by `seqIdx`), the `seqIdx` pointer is incremented. This indicates that we've found a matching element in the sequence.
4. Regardless of whether a match is found, the `arrIdx` pointer always increments to continue scanning through the main array.
5. After the loop, the function checks if the `seqIdx` has reached the end of the `sequence`. If it has, this means all elements of the sequence were found in the array in order, and the function returns `True`. Otherwise, it returns `False`, indicating the provided sequence is not a valid subsequence of the array.

```Python
def isValidSubsequence(array, sequence):
	arrIdx = 0
	seqIdx = 0
	while arrIdx < len(array) and seqIdx < len(sequence):
		if array[arrIdx] == sequence[seqIdx]:
			seqIdx += 1
		arrIdx +=1
	return seqIdx == len(sequence)
	
```

## Solution 2
The `isValidSubsequence` function determines if a given `sequence` can be represented as a subsequence within a larger `array`. 

1. The function initializes a pointer `seqIdx` to track the position within the `sequence`.
2. As the function iterates over each `value` in the `array`, it checks whether the current `value` matches the element of the `sequence` pointed to by `seqIdx`.
3. If a match is found, `seqIdx` is incremented, indicating progression through the sequence.
4. A preliminary check is used at the start of each iteration: if `seqIdx` equals the length of `sequence`, the loop breaks early, signifying that all elements of the `sequence` have been successfully matched.
5. After iterating through the `array`, the function checks if `seqIdx` has reached the end of the `sequence`. If so, it means that all elements of the `sequence` were found in the `array` in the correct order, and the function returns `True`. If not, it returns `False`, indicating the sequence is not a valid subsequence of the array.

```Python
def isValidSubsequence(array, sequence):
	seqIdx = 0
	for value in array:
		if seqIdx == len(sequence):
			break
		if sequence[seqIdx] == value:
			seqIdx +=  1
	return seqIdx == len(sequence)
```