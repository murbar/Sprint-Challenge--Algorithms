# A

```
a)  a = 0
    while (a < n * n * n):
      a = a + n * n
```

`O(n)`

This one is a bit tricky. I added a counter to the code and graphed it to be sure. This first line is `O(1)` and the loop looks like `O(n^3)` at first blush but in the body of the loop we are incrementing a by n^2 so the while loop actually runs `O(n^3) / O(n^2)` with is `O(n)`.

# B

```
b)  sum = 0
    for i in range(n):
      i += 1
      for j in range(i + 1, n):
        j += 1
        for k in range(j + 1, n):
          k += 1
          for l in range(k + 1, 10 + k):
            l += 1
            sum += 1
```

Polynomial time, somewhere between `O(n^3)` and `O(n^4)` according to the graph.

Starting from the inner-most loop, if runs about 10 times no matter the value of `k`, so that's `O(1)`, and the three outer loops run approximately `n` times so our total run time is `O(n) * O(n) * O(n) + O(1)` which simplifies to `O(n^3)`.

# C

```
c)  def bunnyEars(bunnies):
      if bunnies == 0:
        return 0

      return 2 + bunnyEars(bunnies-1)
```

`O(n)`

Every call to `bunnyEars` makes another call to `bunnyEars` recursively with `n + 2` giving us a running time of `O(2n)`, which simplifies to `O(n)`.

# Ex II

Suppose that you have an _n_-story building and plenty of eggs. Suppose also that an egg gets broken if it is thrown off floor _f_ or higher, and doesn't get broken if dropped off a floor less than floor _f_. Devise a strategy to determine the value of _f_ such that the number of dropped eggs is minimized.

Write out your proposed algorithm in plain English or pseudocode and give the runtime complexity of your solution.

So I'm assuming that we want to find the highest floor at which we can throw off eggs and they won't break, and we want to use as few eggs as possible. In that case I would use a divide & conquer strategy of picking a floor `f` between 0 and `n` and checking if an egg dropped from that floor breaks. If it does I would reset `f` to another floor between 0 and initial `f`, and if it does not I would set `f` to a floor between initial `f` and `n` and repeat until I found `f` at which eggs break where `f - 1` egg don't break. This strategy would cost us `log n` eggs for a building of `n` stories.
