# Phone Number Letters Solution

@billma12

The key to solving this problem is to start small. First think about when the input is just 1 digit. This has to be part of the solution no matter what

```python
d = {'2': 'abc', '3': 'def', '4': 'ghi',
     '5': 'jkl', '6': 'mno', '7': 'prqs',
     '8': 'tuv', '9': 'wxyz'}

result = []
for digit in num:
    for c in digit[num]:
        result.append(c)
return result
```
The next step is to think dynamically. When there are 2 digits, we need to concatenate the characters of the 2nd digit to the solution set of the first digit. When there are 3 digits, we need to concatenate the characters of the 3rd digit to the solution set of the first 2 digits, etc... It should look something like below

```python
def phone(num):
    d = {'2': 'abc', '3': 'def', '4': 'ghi',
         '5': 'jkl', '6': 'mno', '7': 'prqs',
         '8': 'tuv', '9': 'wxyz'}

    result = []
    for digit in num:
        if digit not in d:
            continue
        temp = []
        for c in d[digit]:
            if len(result) == 0:
                temp.append(c)
            else:
                for combo in result:
                    temp.append(combo + c)
        result = temp

    return result
```

```
input: '234'
output: ['adg', 'bdg', 'cdg', 'aeg', 'beg', 'ceg', 'afg', 'bfg', 'cfg', 'adh', 'bdh', 'cdh', 'aeh', 'beh', '
ceh', 'afh', 'bfh', 'cfh', 'adi', 'bdi', 'cdi', 'aei', 'bei', 'cei', 'afi', 'bfi', 'cfi']

input: '99'
output: ['ww', 'xw', 'yw', 'zw', 'wx', 'xx', 'yx', 'zx', 'wy', 'xy', 'yy', 'zy', 'wz', 'xz', 'yz', 'zz']

input: '5'
output: ['j', 'k', 'l']
```
