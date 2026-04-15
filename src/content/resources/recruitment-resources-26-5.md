---
title: 'Introduction'
description: 'An introduction to cryptography'
category: 'Cryptography'
order: 1
---


Cryptography is the study of securing and breaking hidden information using patterns, logic, and mathematics. It involves encoding messages so they cannot be understood by unintended parties and finding ways to decode them when possible.

In this roadmap, you will get a hands-on introduction to this world. You will start with simple ciphers, build your math foundation, and eventually understand how real systems like RSA work.

## 1. The Classics
Train your brain to spot hidden structures before the math gets heavy. These are "pencil and paper" ciphers that rely on substitution and transposition.

* **Concepts to Research**: Use Wikipedia to look up Caesar, ROT13, Substitution, Vigenère, One-Time Pad, and RC4 (the XOR one).
* **Tools**: Use the [dcode.fr cipher identifier](https://www.dcode.fr/) to figure out what you are looking at. Use [CyberChef](https://gchq.github.io/CyberChef/) to actually run the decryptions.
* **Reading**: For the best narrative history of this field, read **"The Code Book" by Simon Singh**. It makes the history of the Mary Queen of Scots cipher feel like a thriller.

**Assignment**: Solve [this challenge](https://www.khanacademy.org/computing/computer-science/cryptography/cryptochallenge/a/cryptochallenge-introduction) by Khan Academy. (do discuss this on whatsapp group, i wanna see you all suffer :))

> **IMPORTANT**: **Avoid using AI** for the puzzles. If you let a bot solve the pattern for you, you are sabotaging your own learning.

## 2. The Math Foundation
Cryptography is essentially applied number theory. You cannot skip this part if you want to understand why encryption actually stays secure.

* **Symmetric vs. Asymmetric**: First, learn the difference between using one key to lock/unlock and using a public/private key pair. [Read the breakdown here](https://www.geeksforgeeks.org/computer-networks/difference-between-symmetric-and-asymmetric-key-encryption/).
* **Essential Topics**:
    * **Modular Arithmetic**: Often called "clock math." It is the heart of almost every crypto system.
    * **Fermat's Little Theorem**: Crucial for understanding how we simplify large exponents.
    * **Chinese Remainder Theorem (CRT)**: Used to solve systems of congruences, which is a common trick in breaking RSA.
    * **Greatest Common Divisor (GCD) and Extended Euclidean Algorithm**: You will need these to find "modular inverses."

| Topic | Resource |
| :--- | :--- |
| Modular Arithmetic | [Intro Guide](https://artofproblemsolving.com/wiki/index.php/Modular_arithmetic/Introduction) |
| Fermat's Little Theorem | [The Wiki](https://artofproblemsolving.com/wiki/index.php/Fermat%27s_Little_Theorem) |
| Chinese Remainder Theorem | [The Wiki](https://artofproblemsolving.com/wiki/index.php/Chinese_Remainder_Theorem) |
| Primitive Roots | [Discrete Logarithm Intro](https://en.wikipedia.org/wiki/Primitive_root_modulo_n) |

**Practice**: Create an account on **[CryptoHack](https://cryptohack.org)**. Start with the "Modular Arithmetic" section. It is the gold standard for learning this via coding.

## 3. RSA Mechanics
This is your first "real" encryption algorithm. It relies on the fact that it is easy to multiply two large prime numbers, but incredibly hard to factor the result back into those primes.

* **Watch**: [This video](https://www.youtube.com/watch?v=JD72Ry60eP4) for a visual breakdown of the math.
* **Key Components**: Learn what N (modulus), e (public exponent), d (private exponent), p, and q (primes) are. [Read this guide](https://www.geeksforgeeks.org/computer-networks/rsa-algorithm-cryptography/).
* **New Tool (Factordb)**: If you ever see a small or weak modulus N, check [factordb.com](http://factordb.com/). It is a database of already-factored numbers.
* **Coding RSA**: Try to write a Python script that can encrypt and decrypt a message using the RSA formula: c = m^e mod N.

## 4. Modern Horizons (Next Steps)
Once RSA clicks, the world of modern cryptography opens up. If you are feeling ambitious, look into these:

* **Diffie-Hellman Key Exchange**: How two people can create a shared secret over an insecure line.
* **Elliptic Curve Cryptography (ECC)**: This is what protects your Bitcoin and your WhatsApp messages today. It is more efficient than RSA.
* **Digital Signatures**: How we prove a message actually came from the sender and wasn't changed.

## 5. Further Resources and Problems
If you want to keep testing your skills, these sites offer a progression from "easy" to "math genius."

* **[PicoCTF](https://picoctf.org/)**: Go to the "Cryptography" category. They have excellent entry-level RSA and Vigenère problems.
* **[Cryptopals](https://cryptopals.com/)**: This is a set of challenges designed to teach you how to break real-world crypto. Very coding-heavy.
* **[OverTheWire: Krypton](https://overthewire.org/wargames/krypton/)**: A wargame focused specifically on ciphers.
* **[id0-rsa](https://id0-rsa.pub/)**: A dedicated platform for RSA and beyond.
* **[SageMath](https://www.sagemath.org/)**: Eventually, you will want to learn Sage. It is a mathematical software system that makes complex modular arithmetic and elliptic curve math much easier to script.
