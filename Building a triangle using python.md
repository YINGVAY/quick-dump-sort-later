Me and lactose embarked on the journey of creating a triangle with variable size using the python language

```python
	height = 5
	for number in range (1, height + 1):
	  spaces = " " * (height - number)
	  stars = "*" * (2 * number - 1)
	  print (spaces + stars)
```

`(height = 5)` is setting "height" equal to 5, so effectively you could add height + 5 and get 10

`for number in range( 1, height + 1)` The for loop assigns each number in the sequence (from `range`) to the variable `number`, one at a time. For each value of `number`, it runs the indented code block

`range` (start) The number to start from, in this case 1. (stop) The number to stop before, not included in this sequence. (step) The amount to increment or decrement by.

`print` Simply prints a string like `print("get wrecked"`

[[2025-01-11 (First day of taking notes for 365 days)]]




