# bca-store

We intercepted a message between two agents from a terrorist group known as 0x4556494c. We think it might contain some useful information, so we'd like you to crack it. Here is the message.

BEGIN TRANSMITION

Dear Agent Reffef,

I have attached the super secret plans for operation 0x576f726b206f6e207468652070757a7a6c652c2073746f702072656164696e672068657821.
You will need to decode it first though.

The rules are simple:

A line is "viable" if the length of a line is divisible by 3, and the line does not contain the `&` character. 

For every viable line, you will grab the `n`th character, 
where `n` is the corresponding number at the top of the file (Counting from one!) 
The first viable line will use the first number, etc.

Put all the letters together to find the answer!  

\- Agent Doposi

END TRANSMITION

made by: @sebwit20

File: flag.txt

## Solution

```python
output = ""
with open("flag.txt", "r") as f:
    lines = f.readlines()
    nlist = map(int, lines[0].split())
    instructions = lines[1:]
    idx = 0
    for line in instructions:
        line = line.strip()
        if len(line) % 3 == 0 and line.find("&") == -1:
            output += line[nlist[idx] - 1]
            idx += 1

print output
```

Flag: ```bcactf{f0110w_tH3_r00lz_<3_l0ve_m3_pls``` 