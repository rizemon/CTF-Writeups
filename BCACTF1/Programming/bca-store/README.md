# bca-store

You are a cashier for a small store that sells a few items. Coming up is the annual sale, and you really don't want to do that much math. So, being you, you decide to automate it.

Items:

A: $45, no sale  
B: $52, buy one get one 10% off  
C: $67, buy one get one half off  
D: $75, buy two get one free  
Input:  

What the customer ordered, separated by spaces.  
The amount the customer paid.  
For example, C B B C A 250.  

The input file is attached. If we had the above twice, then you can use   the following to test on your local machine:  

input.txt:  

C B B C A 250  
D A B B 250  
D D D D D A B 390  
$ cat input.txt | ./script.py  
Your program should print the customer's change (i.e. return to stdout), if applicable, or -1 (the number) if they don't have enough money. The above example should result in:  

5.70  
31.20  
-1  
Round to the nearest hundredths place.  

You should submit your answer as one string, with each input line's result separated by a space.

For example, the above output should be formatted as follows to be accepted: 5.70 31.20 -1

File: input.txt

## Solution

A typical programming question so lets get to it. One thing to take note is that if there is not enough money, print -1, else print the change to the nearest 2 d.p.

```python
prices = {
	"A": 45,
	"B": 52,
	"C": 67,
	"D": 75
}

def calc(items):
    total = 0
    order = {
        "A": 0,
        "B": 0,
        "C": 0,
        "D": 0
    }
    for item in items:
        order[item] += 1
    total += order["A"] * prices["A"]
    total += order["B"]/2 * 0.9 * prices["B"] + (order["B"] - order["B"]/2) * prices["B"]
    total += order["C"]/2 * 0.5 * prices["C"] + (order["C"] - order["C"]/2) * prices["C"]
    total += order["D"]/3 * 0.0 * prices["D"] + (order["D"] - order["D"]/3) * prices["D"]
    return total

with open("input.txt", "r") as f:
    for line in f.readlines():
        tokens = line.split()
        items = tokens[:-1] 
        paid = int(tokens[-1])
        total = calc(items)
        if paid < total:
            print "-1",
        else:
            print "%.2f"% (paid - total),
```

Flag: ```5.70 -1 1.00 75.00 -1 77.40 -1``` 