202406071019
Status: #learning
Tags: [[Algorithms]]
# Recursion

```python {hl_lines=[1]}
def factorial(x):
	if x == 1:                        # Base Case
		return 1
	else:                             # Recursive Case
		return x * factorial(x - 1)
```

You can use something called [[Tail Recursion]]
### Recap
- Recursion is when a function calls itself
- Every recursive function has 2 cases:
	 1. Base Case
	 2. Recursive Case
- A stack has two operations: push and pop
- All function calls go onto the call stack
- The call stack can get very large which takes up a lot of memory

# References
"[[Grokking Algorithms]]" by Bhargava > Chapter 3 > pg. 50