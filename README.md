# Modular Arithmetic-Based Cipher

This project demonstrates the encryption and decryption process of the plain text "key" using a modular arithmetic-based cipher.

## Overview

The cipher utilizes modular arithmetic for secure message encryption and decryption. While the example uses small prime numbers for simplicity, real-world applications would involve much larger primes for enhanced security.

---

## Step-by-Step Explanation

### 1. Convert Characters to ASCII Values

Each character in "key" is converted into its corresponding ASCII value:

| Character | ASCII Value |
|-----------|-------------|
| k         | 107         |
| e         | 101         |
| y         | 121         |

So, the plain text "key" is represented as:

{107, 101, 121}


---

### 2. Key Setup

- Let’s take two small prime numbers  p = 17  and  q = 19 .
- Compute  N = p * q = 17 * 19 = 323 .
- Let’s choose an encryption key  K = 5 , which is coprime with  (p-1) * (q-1) = 16 * 18 = 288 .

---

### 3. Encryption Process

Each ASCII value \( P \) is encrypted using the formula:

\[
C = (P * K) mod N
\]

Where:
-  P  is the ASCII value of the character.
-  K = 5  is the encryption key.
-  N = 323 .

#### Encrypted Values:

- k (107) →  C = (107 * 5) mod 323 = 535 mod 323 = 212 
- e (101) →  C = (101 * 5) mod 323 = 505 mod 323 = 182 
- y (121) →  C = (121 * 5) mod 323 = 605 mod 323 = 282  

| Character | ASCII Value | Encrypted Value (\( C \)) |
|-----------|-------------|---------------------------|
| k         | 107         | 212                       |
| e         | 101         | 182                       |
| y         | 121         | 282                       |

The encrypted message is:

{212, 182, 282}


---

### 4. Decryption Process

To decrypt, we calculate the modular inverse \( K^{-1} \) of \( K \mod (p-1)(q-1) \) using the Extended Euclidean Algorithm. For \( K = 5 \) and \( (p-1)(q-1) = 288 \), the modular inverse is:

\[
K^{-1} = 173
\]

Each ciphertext value \( C \) is decrypted using the formula:

\[
P = (C * K-1) mod N
\]

Where:
-  C  is the ciphertext.
-  K-1 = 173  is the decryption key.
-  N = 323 .

#### Decrypted Values:

- 212 →  P = (212 * 173) mod 323 = 36676 mod 323 = 107  → k
- 182 →  P = (182 * 173) mod 323 = 31486 mod 323 = 101  → e
- 282 →  P = (282 * 173) mod 323 = 48786 mod 323 = 121  → y

| Encrypted Value (\( C \)) | Decrypted ASCII Value (\( P \)) | Character |
|---------------------------|---------------------------------|-----------|
| 212                       | 107                             | k         |
| 182                       | 101                             | e         |
| 282                       | 121                             | y         |

The decrypted message is:

{107, 101, 121} = "key"


---

## Conclusion

- **Original Text**: "key"
- **Encrypted Message**: `{212, 182, 282}`
- **Decrypted Message**: "key"

This example illustrates the process of encryption and decryption using a modular arithmetic-based cipher. For real-world applications, larger prime numbers \( p \) and \( q \) should be used for better security.

---

## Note

This project demonstrates the concept of modular arithmetic in cryptography. It is intended for educational purposes, and real-world implementation should follow advanced cryptographic standards.
