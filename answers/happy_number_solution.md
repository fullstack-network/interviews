# Happy Number Solution

@billma12

The key to this problem is knowing when a number is unhappy. We are eventually going to arrive at
a sum that is equal to 1 or we are going to arrive at a number that we've
encountered before. If the latter, then the number is unhappy.

```
ex 1) 123 => 1^2 + 2^2 + 3^2 = 1 + 4 + 9 = 13
      13 => 1^2 + 3^2 = 1 + 9 = 10
      10 => 1^2 + 0^2 = 1 + 0 = 1 (happy)

ex 2) 42 => 16 + 4 = 20
      20 => 4 + 0 = 4
      4 => 16
      16 => 1 + 36 = 37
      37 => 9 + 49 = 58
      58 => 25 + 64 = 89
      89 => 64 + 81 = 145
      145 => 1 + 16 + 25 = 42 (unhappy)
```

```python
# recursive solution
def isHappy(n):
    def helper(num, answers):
        total = 0

        while num > 0:
            total += (num % 10) ** 2
            num = num // 10

        if total == 1:
            return True
        elif total in answers:
            return False
        else:
            answers.append(total)
            return helper(total, answers)

    return helper(n, [])

# iterative solution
def isHappy2(n):
    ans = []
    total = 0

    while True:
        while n > 0:
            digit = n % 10
            total += digit ** 2
            n = n // 10

        if total == 1:
            return True
        if total in ans:
            return False

        ans.append(total)
        n = total
        total = 0

```

