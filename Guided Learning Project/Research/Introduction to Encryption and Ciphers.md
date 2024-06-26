
# Introduction 
As I started this project my Learning Facilitator asked me, what is a cipher and I realised I did not even know how to describe it. So I started my research on what a cipher is.

The terms cipher and encryption are often interchangeable. 


<a name="history"></a>
## History & Their Importance
The first cipher was created by Julius Caesar in times of war where information needed to be kept secret so that even if the enemy got their hands on the message, they would not be able to understand it. He rotated each letter of the plaintext forward by 3 places such that A became D, B became E, etc. Even now, encryption is used to secure sensitive information before it is sent over modern communication. 
An example of how important ciphers are, is when Alan Turing cracked the German's Enigma cipher, which was a significant factor leading to the German's defeat. The decryption of German communications provided the Allies with crucial information about German military plans, strategies, and activities.

- [Types of Encryption Methods](#encrypt_mtd)
  - [Substitution Ciphers](#substitution)
    - [Monoalphabetic Ciphers](#monoalphabetic)
    - [Homophonic Ciphers](#homophonic)
    - [Polygraphic Ciphers](#polygraphic)
    - [Polyalphabetic Ciphers](#polyalphabetic)
    - [Transposition Ciphers](#transposition)
  - [Symmetric Key Encryption](#symmetric)
  - [Asymmetric Key Encryption](#asymmetric)
  - [Hashing](#hashing)
    - [SHA](#sha)
    - [MD5](#md5)
    - [Salting](#salting)
    
- [Cipher Cracking](#cipher_cracking)
  - [Frequency Analysis](#freq_analysis)
  - [Pattern Recognition](#pattern_recog)
  - [Difficult to Reverse Mathematical Operations]
- [Making Ciphers Hard to Crack]
  - [Trapdoor functions]
  - [More Characters or Mapping Multiple Characters to 1 Plaintext Character]

<a name="encrypt_mtd"></a>
# Types of Encryption Methods

<a name="substitution"></a>
## Substitution Ciphers 
The ciphers under this category of "substitution" replace each letter, in a way the identity of the letters changes. 

<a name="monoalphabetic"></a>
### Monoalphabetic Ciphers
Generally, a simple one-to-one mapping of letters is used. For example, each 'A' in the plaintext is replaced by the same letter in the ciphertext.

Examples include: 
#### Simple Substitution Cipher
As stated above, it replaces one letter with another. For example, the plaintext letter 'A' would be replaced with the letter 'L', 'B' with 'P', 'C' with 'J' etc.

![Table showing letters in an exmaple of Simple Substitution Cipher](../docs/assets/img/sub_cipher.png)

#### Caesar Cipher: 
This cipher is named after the cipher Julius Caesar created. It is also known as Shift or Rotation Cipher as each letter in the plaintext is shifted or rotated forward by a fixed number of positions (also called the key) down the alphabet. For example, if the key is 3, 'A' in the plaintext would be 'D' in the ciphertext. 

![Table showing letters in an exmaple of Caesar Cipher](../docs/assets/img/caesar.png)

#### Atbash Cipher
The earliest instances of this cipher are in the Hebrew Bible, the Book of Jeremiah. The exact reason for the usage of the cipher is not known. It could have been to protect the prophet or the later scribe, as the prophet, Jeremiah, was given the task of publically announcing Cod's punishment on the nations, which included the Babylonian empire, in Jeremiah 25. “<sup>15</sup>This is what the LORD, the God of Israel, said to me: ‘Take from my hand this cup filled with the wine of my wrath and make all the nations to whom I send you drink it. . . . <sup>26</sup>And after all of them, the king of Sheshak will drink it too.'”

The alphabet would be reversed, such that A becomes Z, etc.

![Table showing letters in Atbash Cipher](../docs/assets/img/atbash.png)

##### Code
```
import string

msg = input('Text: ')
lower = list(string.ascii_lowercase)
upper = list(string.ascii_uppercase)
result = ''

for letter in msg:
    if letter in lower:
        result += lower[25 - lower.index(letter)]
    elif letter in upper:
        result += upper[25 - upper.index(letter)]
    else:
        result += letter
print(result)

```


#### Affine Cipher
Each letter is mapped to its numeric equivalent, multiplied by a constant, and then shifted by another constant.

For example, if f(x) is the result, x is the numeric equivalent of the letter, a is the multiplication constant and b is the rotation constant, the formula would be:
f(x) =  (ax + b) mod 26
And y has to be a prime number so it can be reversed. 



### Geometric Cipher
In this category, the letters are replaced with geometric symbols.

#### Pigpen Cipher 
It is populated by the Freemasons, who used it so much that it is sometimes referred to as the Freemason's cipher. The Freemasons began using it in the early 18th century to keep their records of history and rites private, and for correspondence between lodge leaders.

![Pigpen Cipher](../docs/assets/img/pigpen.png)


#### Rosicrucian Cipher 
A variation of the Pigpen cipher that was used by the Rosicrucian Brotherhood. 

![Rosicrucian  Cipher](../docs/assets/img/rosicrucian.png)

#### Templar Cipher
The Templar Cipher is said to have been used by the Knights Templar, a group of rich warrior monks, who needed a way to encrypt their notes so that if bandits robbed travellers, the note would be useless to the bandits. For the Knights Templar, the notes told them how much money the person had stored with them. 

![Templar Cipher](../docs/assets/img/templar.png)

#### Mixed Alphabet Ciphers
Each letter is replaced by a corresponding letter from a mixed-up or randomly generated alphabet.


##### Vatsyayana Cipher
The 26 letters are paired into 13 pairs, and substitution is done using those pairs. An example of this is the one given below. 

![Table showing letters in an exmaple of Vatsyayana Cipher](../docs/assets/img/vatsyayana.png)

From the example above, the letter 'A' would be substituted with 'L' and vice versa, 'B' with the letter 'P', etc.


<a name="homophonic"></a>
### Homophonic Ciphers
Multiple ciphertext characters can be used to represent a single plaintext character. This introduces ambiguity and makes frequency analysis more challenging.

The example in the website below uses numbers to replace letters and for each % the frequency a letter would typically appear, one number is assigned to them. For example, if A has an 8% chance of appearing in English texts, it would be assigned 8 numbers. 

https://www.simonsingh.net/The_Black_Chamber/homophonic_cipher.html

<a name="polygraphic"></a>
### Polygraphic / Block Ciphers
#### Hill Cipher 


#### Playfair Cipher (digraph cipher)


#### Polybios Square Cipher
It is named after the ancient Greek historian Polybios. Since the Greek alphabet has 25 letters, the 5x5 square was used, where the alphabet was written in a grid format. When using English letters, I and J are typically combined and given 1 space. 

![Polybios Square](../docs/assets/img/polybios.png)

<a name="polyalphabetic"></a>
### Polyalphabetic Ciphers
As the name implies, more than 1 set of the alphabet is used. In the 2 examples below, they use the 2 sets of the English alphabet (Tabula recta) to encrypt the message. 

![Tabula recta](../docs/assets/img/tabula_recta.png)

#### Vigenère Cipher
We encrypt character by character of the plaintext and the key is repeated to fit the length of the plaintext. We would find the column for the plaintext letter in the top row and the row of the key letter along the leftmost column, we would trace till the row and column intersect. 

For example, if the plaintext is 'we are discovered' and the key is 'flee'. The key would be repeated to fit the length of the plaintext. We would find among the column headers for 'W' and the row header for 'F', which gives the letter 'B'. This process would be repeated for each character of the plaintext message and gives the ciphertext 'BP EVJ OMWHZZIWPH' if the punctuation is preserved. 

![Example of using tabula recta for Vigenère Cipher](../docs/assets/img/vigenere_eg_table.png)

![Example of Vigenère Cipher](../docs/assets/img/vigenere_eg.png)

#### Autokey Cipher
It is a similar version to Vigenère Cipher but the plaintext is added onto the back of the key so instead of the key alone being repeated for the length of the plaintext, the key is now longer. 

For example if the plaintext is 'we are discovered' and the key is 'flee'. The plaintext would be added onto the key, becoming a key stream of 'fl eew earediscov'. The rest of the process is the same as Vigenère Cipher, and gives the ciphertext 'BP EVA HIJGRDWTSY' if the punctuation is preserved. 

![Example of Autokey Cipher](../docs/assets/img/autokey.png)


<a name="transposition"></a>
## Transposition Ciphers
The ciphers under this category of "transposition" changes the position of the letters but the letters' "identities" do not change. For example, take the plaintext to be "Hello world!", there are 3 instances of the letter "l". The resulting ciphertext would still have 3 instances of the letter "l". 

Examples:
<a name="rail_fence"></a>
#### Rail Fence Cipher: (Also known as Zigzag cipher)
The plaintext is written in a zigzag pattern across a set number of rails of the fence (which are the lines) and then each line of text (each rail) is appended to the ciphertext. 

The characters would start going downwards and diagonally across the rails and at the bottom, move upwards and diagonally across. 

An example is using the plaintext 'WEAREDISCOVERED' with the number of rails (horizontal rows) being 3.

![Table showing letters in an example of Rail Fence Cipher](../docs/assets/img/rail_fence.png)

The cipher would read across each rail and append the text to get the ciphertext, 'WECRERDSOEEAIVD'.

Spacing is optional in the ciphertext as it would not be related to the spacing in the plaintext and would not give away any information. The ciphertext can be split into groups of 5 using spacings, so that the ciphertext is more readable. 



##### Code
```
rails = input('Enter your number of rails: ')
while rails.isdigit() == False:
    print('\nPlease try again, the number of rails should be an integer.')
    rails = input('Enter your number of rails: ')

rails = int(rails)
print()
plaintext = input('Enter your plaintext: ').strip()
ciphertext = [''] * rails

down = True
row = 0
for index in range(len(plaintext)):
    # Ignores spacing in plaintext
    if plaintext[index].isspace():
        continue
    else: 
        ciphertext[row] += plaintext[index]

    if row < (rails-1) and down == True:
      row += 1
    elif row > 0 and down == False:
        row -= 1

    if row == 0 or row == (rails-1):
        down = not down

ciphertext = ''.join(ciphertext)

### Optional (for the spacing) ###
for index in range(0, len(ciphertext)):
    if index % 6 == 0:
        ciphertext = ciphertext[:index] + ' ' + ciphertext[index:]

ciphertext = ciphertext.strip()
print()
print(ciphertext)
```

<a name="scytale"></a>
#### Scytale Cipher
One of the oldest known examples is the Spartan scytale, where the Ancient Greeks would wrap a ribbon around a cylindrical rod of uniform circumference before writing a message on the ribbon horizontally. The key would set the number of characters in each (horizontal) row. The message would be the (vertical) columns appended together. 

For example, if the plaintext is 'WE.ARE.DISCOVERED.FLEE.AT.ONCE.', the message would be written, while ignoring the separator. 

![Table showing letters in an example of Scytale Cipher](../docs/assets/img/scytale.png)

Then when the ciphertext is combined together, the separator would be added back in the same position so that the recipient would be able to reconstruct the message. 


<a name="columnar_transposition"></a>
#### Columnar Transposition Cipher
This cipher adds a level of complexity to the scytale cipher, instead of taking the text from the left-most to the right-most columns, the order of which column to take the text from (also known as the key for this cipher) is changed. 

In the example below, it is similar to the one for the Scytale cipher but the key, which sets the order is 362145. The ciphertext would be 'AC.DTD.EECESEAWIR.EERO.FO.EVLN'.

![Table showing letters in an example of Columnar Transposition Cipher](../docs/assets/img/columnar_transposition.png)


<a name="matrix_transposition"></a>
#### Matrix Transposition Cipher


<a name="symmetric"></a>
## Symmetric Key Encryption
A single key is used to encrypt and decrypt. Symmetric keys are usually 128 or 256 bits long. The longer the key, the harder it is to crack. For example, a 128-bit key has around 340,000,000,000,000,000,000,000,000,000,000,000,000 encryption code possibilities. This makes brute force attacks more time-consuming and it becomes a less realistic approach to crack such a key.

<a name="des"></a>
### Data Encryption Standard (DES)

<a name="aes"></a>
### Advanced Encryption Standard (AES)

<a name="asymmetric"></a>
## Asymmetric Key Encryption
It uses a public-private key pairing such that data that has been encrypted with the public key can only be decrypted using the private key. The sender and recipient would have their own unique public-private key pair. As the name of the keys implies, the public key is shared openly, while the private key is kept confidential.


<a name="rsa"></a>
### Rivest–Shamir–Adleman (RSA)

<a name="ecc"></a>
### Elliptic Curve Cryptography (ECC) 

<a name="hashing"></a>
## Hashing
It is a one-way encryption to secure data. It is one way as the data is encrypted using a formula, of which the results lose a lot of data, that would be needed to be able to reverse the hashing. 
Hashing is used to secure data that does not need to be retrieved, such as passwords. A password is hashed and then saved in the database. This is done so that if the database is leaked or compromised, the attacker cannot use the retrieved hash to log in. 

### Examples of hashes:

<a name="sha"></a>
#### Secure Hash Algorithm (SHA)
SHA256 is currently the industrial standard. It is a hashing algorithm that encrypts text of any length into a fixed-size string of 256 bits (32 bytes) and is a part of the SHA 2 algorithm family. 
In comparison to SHA512, it requires less bandwidth to store and transmit, takes up less memory space and in many cases, uses less processing power to compute. 

However, SHA512 has greater collision resistance, which may need to be considered in the future, when a quantum computer would be able to crack hashes.

Since SHA-256 produces a 256-bit hash, while SHA-512 produces a 512-bit hash, the longer hash length of SHA-512 provides a larger output, making it more resistant to certain types of cryptographic attacks, such as brute-force and collision attacks.

Additionally, different hardware favours different functions. SHA512 is generally faster on 64-bit processors and SHA256 is faster on 32-bit processors.

<a name="md5"></a>
#### MD5
The MD5 message-digest algorithm is one of the most commonly known hashes as it is widely used. However, it is not up to industrial standards since it is not as secure as SHA256 since hash collision is possible. MD5 is a hashing algorithm that produces a 128-bit hash value.

MD5 is still used as it would be difficult for those who have used it for years, to make changes to the entire database. Also, even though MD5 hashes may have collisions, it takes a lot of time and effort to get a collision, and it is better to have hashed data rather than data that is stored in plaintext. 

<a name="hash_collision"></a>
### Hash collision 
This occurs when hashing 2 texts gives the same result. However, this is very hard to do as changing just 1 character from the plaintext would change the hash. One would need a lot of trial and error to see how each change affects the hash. 


<a name="salting"></a>
### Salting
Adding a unique value (salt) to the data before hashing, enhances security by preventing precomputed attacks.

<a name="cipher_cracking"></a>
# Cipher Cracking
Written below are some methods frequently used to crack or analyse ciphers. 

<a name="freq_analysis"></a>
## Frequency Analysis
It is typically used to break substitution ciphers. 

It studies the frequency of letters or groups of letters in the ciphertext, based on the fact that in any written language, certain letters and combinations of letters occur with varying frequencies. For example in the English language, the letters E, T, A, and O are the most common. 
One would identify the most often occurring letters in the ciphertext and theorise which letters those in the ciphertext are mapped to. They may then be able to recognise patterns or words in the partially decoded text to identify more letters. 

<a name="pattern_recog"></a>
## Pattern Recognition 
Identifying patterns in ciphertext can provide insights into the underlying structure of a substitution or transposition cipher. After a letter is discovered, the text can then be checked for possible letters after it. For example for the letter 't', 'h' is often the letter after it. 


## Mathematical Operations that are difficult or impossible to reverse 
An example of a function that cannot be reversed is matrix multiplication since there is no matrix division. 


# How to make cipher harder to crack
## Trapdoor functions
They refer to operations that are easy to calculate in one direction but difficult to reverse without special knowledge. 

One example is modulus (%), which gets the remainder from a division. It would be difficult to reverse the modulus equation as without knowing the divisor and quotient, it is impossible to guess what the original number is. 

## Introducing more characters or mapping multiple characters to a plaintext character
This would reduce the effectiveness of frequency analysis, which analyses the frequency of letters occurring in any English text to give hints as to the identity of the plaintext letter. 

Such as what is done in homophonic ciphers, since for each percentage a character will 
