---
title: 'Cryptography II'
description: 'RSA exploits, public key algorithms, hashing, Diffie-Hellman, and AES'
category: 'Cryptography'
order: 2
---

> **Prerequisites:** Familiarity with the basics of Cryptography and RSA. Refer [here](https://wiredin.pclub.in/resources/recruitment-resources-26-5/).
> **Focus:** RSA exploits, public key algorithms, hashing, Diffie-Hellman, and AES.

---

## 1. Hashing

Hashes are the backbone of how passwords are stored in databases - not as plaintext, but as fixed-length digests that cannot be reversed.

**Key properties of hash functions:**
- **One-way** - you cannot derive the original input from the hash
- **Collision-resistant** - two different inputs should not produce the same hash
- **Deterministic** - same input always yields the same output

### Resources
- [Video: Hash Functions Explained](https://www.youtube.com/watch?v=b4b8ktEV4Bg)
- [Blog: Cryptographic Hash Functions - TutorialsPoint](https://www.tutorialspoint.com/cryptography/cryptography_hash_functions.htm)
- [MD5 Collision Demo](https://www.mscs.dal.ca/~selinger/md5collision/) - a classic example of why MD5 is considered broken

---

## 2. Real-World RSA Exploits

RSA, while foundational, has several well-documented vulnerabilities that are actively exploited in CTFs and real-world scenarios.

### Resources
- [RSA Attack Survey Paper - Dan Boneh, Stanford](https://crypto.stanford.edu/~dabo/papers/RSA-survey.pdf) *Highly recommended - covers major RSA exploits in depth*
- [RsaCtfTool - GitHub](https://github.com/RsaCtfTool/RsaCtfTool) - a collection of automated RSA exploit scripts for CTF challenges

---

## 3. Diffie-Hellman Key Exchange

Diffie-Hellman is a foundational protocol that allows two parties to establish a shared secret over a public channel - without ever transmitting the secret itself.

### Resources
- [Video: Diffie-Hellman Explained](https://www.youtube.com/watch?v=85oMrKd8afY) *Great intuition-building video*
- [CryptoHack: Public Key Cryptography - Diffie-Hellman Module](https://cryptohack.org/courses/public-key/course_details/)
- [Blog: Implementing Diffie-Hellman - GeeksForGeeks](https://www.geeksforgeeks.org/computer-networks/implementation-diffie-hellman-algorithm/)

---

## 4. AES (Advanced Encryption Standard)

AES is the gold standard for symmetric encryption, widely used in TLS, file encryption, and beyond.

### Resources
- [Video: AES Explained](https://www.youtube.com/watch?v=C4ATDMIz5wc) *Great introductory video*
- [CryptoHack: AES Module](https://cryptohack.org/courses/) *(Very optional)*

---

## Recruitment Note

> For recruitment, it is **strongly preferred** that you complete the **[CryptoHack Public-Key Cryptography module](https://cryptohack.org/)** at minimum.