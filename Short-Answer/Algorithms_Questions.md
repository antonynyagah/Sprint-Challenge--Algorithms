# Analysis of Algorithms

## Exercise I

Give an analysis of the running time of each snippet of
pseudocode with respect to the input size n of each of the following:

```python
a)  a = 0
    while (a < n * n * n):
      a = a + n * n
```


```
b)  sum = 0
    for i in range(n):
      j = 1
      while j < n:
        j *= 2
        sum += 1
```

```
c)  def bunnyEars(bunnies):
      if bunnies == 0:
        return 0

      return 2 + bunnyEars(bunnies-1)
```

## Exercise II

Suppose that you have an n-story building and plenty of eggs. Suppose also that an egg gets broken if it is thrown off floor f or higher, and doesn't get broken if dropped off a floor less than floor f. Devise a strategy to determine the value of f such that the number of dropped + broken eggs is minimized.

Write out your proposed algorithm in plain English or pseudocode AND give the runtime complexity of your solution.

U   -   We want to find the lowest floor at which an egg would break if thrown from that floor
        To do that we need to find the last floor that the egg doesn't break, and the first floor that it does
P   -   Divide and conquer with binary search
E--
drop an egg on the first floor
-if the egg breaks then you know f is 0
-if the egg does not break:
    First halving
    go to the middle floor of the building
    -if even number then the lower middle floor (this is how we will handle division moving forward)
    drop an egg
    -if the egg does not break:
        --this floor is considered your bottom floor 
        --then go to the middle of the current floors and top floor drop an egg
        --do this until the egg breaks
    -if the egg breaks:
        --this floor is now considered your top floor
        --go back down to the middle of the bottom floor and current floor
        --drop an egg
## --From here we will follow the rules set out above 
-we follow these steps until we get find the last floor that the egg doesn't break, and the first floor that it does
In a building of 100 floors, if the f floor was 66 we would find it in len[50, 75, 62, 68, 65, 66] = 6 steps
The runtime complexity of a binary search tree is O(logn) 