# 1+1=window

hex+hex=hex

credit: [@blackpearl]

File: one.txt, two.txt

## Solution

Each of the files contained a list of hex values delimited with space. According to the description, we probably need to add go through each value in the first file and sum it with its corresponding value in the second file to get the flag.

```python
with open("one.txt", "r") as f1:
    with open("two.txt", "r") as f2:
        numlist1 = [int(c, 0) for c in f1.read().split()]
        numlist2 = [int(c, 0) for c in f2.read().split()]
        output = ""
        for idx in range(len(numlist1)):
            output += chr(numlist1[idx] + numlist2[idx])
print output
```

Flag: ```bcactf{1_h0p3_y0u_us3_pyth0n}``` 