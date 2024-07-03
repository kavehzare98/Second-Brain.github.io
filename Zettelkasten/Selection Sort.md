202406061208
Status: #learning
Tags: [[Algorithms]]
# Selection Sort

```python {hl_lines=[1]}
def findSmallest(arr):
	smallest = arr[0] # Stores the smallest value
	smallest_index = 0 # Stores the index of the smallest value
	for i in range(1, len(arr)):
		if arr[i] < smallest:
			smallest = arr[i]
			smallest_index = i
	return smallest_index

def selectionSort(arr): # Sorts an array
	newArr = []
	for i in range(len(arr)):
		smallest = findSmallest(arr) # Finds the smallest element in the
		newArr.append(arr.pop(smallest)) # array, and adds it to the new array
	return newArr

# Test Case
print(selectionSort([5, 3, 6, 2, 10]))
```

### Big O - O(n^2)
# References
"[[Grokking Algorithms]]" by Bhargava > Chapter 2 > pg. 35