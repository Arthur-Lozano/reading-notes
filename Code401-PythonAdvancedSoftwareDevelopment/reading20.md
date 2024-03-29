## Introduction to Cryptography

### Understanding Ciphers

- Cryptography at its most fundamental level, requires two steps: encryption and decrption. 
- The encryption process uses a cipther in order to encrypt plaintext and turn it into a ciphertext.
- Decryption, on the other hand, applies the same cipher to turn cipthertext back into plaintext.

### Encryption

- The process of making text secret is call Encryption.
- Ceasar cipher, the shift cipher, is one of the simplest and most widely known encryption techniques. He would shift the letters in the alphabet by 3 spaces.
- The CC is one example of a larger class of techniques called Substitution ciphers.
- It is a substitution cipher in which each letter in the plaintext is replaced by a letter some fixed number of positions down the alphabet.
- Shift the alphabet 6 positions and "SECRET MEETING AT THE PALACE" now becomes "YKIXKZ SKKZOTM GZ ZNK VGRGIK"
- Permutation Ciphers: columnar transposition cipher - take a messaage and put letter into a grid, read the letter from a different order from bottom left to top.
- The knew letter ordering called permutation is the new message. ORdering direction and the grid size serves as the key.


### Decrypting

- The processs of reversing encrypted text is call decryption.
- messagers has to know the algorithm and the amount to shift for them to decode the message.

### Polymorphism

- Polymorphism is bascially a ciphter that changes itself with each use. Meaning that  each time is is used, it produces a different set of results.
- Polymorphism is most commonly used in cipher algorithms to encrypt computers, software, and cloud-based information.


### Types of Cryptography

#### Hashing
- changes a messages into an unreadable string of text for the purpose of verifying the message's contents, not hiding the message itself.
- Commonly used to protect the transmission of software and large files where the publisher of the files and software offers them for download.

### References
- https://www.khanacademy.org/computing/computers-and-internet/xcae6f4a7ff015e7d:online-data-security/xcae6f4a7ff015e7d:data-encryption-techniques/a/encryption-decryption-and-code-cracking
- https://en.wikipedia.org/wiki/Caesar_cipher