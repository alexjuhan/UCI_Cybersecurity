# ASCII_decryption

Given a modulus of n = 10403, I have decrypted eight ASCII characters (Using 'A' = 65, 'B' = 66, ... , 'Z' = 90):

                                7427,126,126,9196,7367,126,6642,4744

The private exponent is d = 8743. Use d to decrypt and recover the plaintext. Please post the decrypted word.


```
#p = 101

#q = 103

#n is the modulus
#n = p*q
#p and q are always prime factors
n = 10403

#d is the decryption exponent
d = 8743



#φn = (p-1)*(q-1)

#use cypher for each number and it will decode it
#cypher represents the encrypted numbers
cypher = 7427

#in python ** is the notation for the exponent operator, since the ^ operator is used to invoke an exclusive-or operation
#m in this case represents the decrypted number
m = cypher**d % n

print(m)

#use this var to identify the associated character with the ASCII number
decrypted = chr(m)

print(decrypted)
```