# Reverse Search Algorithm

Written by: Tux

Reverse Search Algorithm

WWPHSN students, gotta get these points to boost your grade.

n = 561985565696052620466091856149686893774419565625295691069663316673425409620917583731032457879432617979438142137  
e = 65537  
c = 328055279212128616898203809983039708787490384650725890748576927208883055381430000756624369636820903704775835777

## Solution

If you look at the first letter of each word in the challenge name, you get "RSA". Lets get cracking. I am going to use the sample solution from a CTF that I had participated in before.

```python
#!/usr/bin/env python3

e = 65537
c = 328055279212128616898203809983039708787490384650725890748576927208883055381430000756624369636820903704775835777
p = 29
q = 19378812610208711050554891591368513578428260883630885898953907471497427917962675301070084754463193723428901453

n = p*q
phi = (p-1)*(q-1)

# Took from SO
def egcd(a, b):
    if a == 0:
        return (b, 0, 1)
    g, y, x = egcd(b%a,a)
    return (g, x - (b//a) * y, y)

def modinv(a, m):
    g, x, y = egcd(a, m)
    if g != 1:
        raise Exception('No modular inverse')
    return x%m

def decimalToAscii(num):
    tmp = num.to_bytes((num.bit_length() + 7) // 8, 'big')
    return tmp.decode('ascii')

d = modinv(e, phi)

print(decimalToAscii(pow(c, d, n)))
```

Flag: ```hsctf{y3s_rsa_1s_s0lved_10823704961253}```

## Reference
https://github.com/DISMGryphons/GryphonCTF2018-Challenges/blob/abe44291f71b51a6634f013b0a2f33b70b63b205/challenges/crypto/Primer/solution/solve.py