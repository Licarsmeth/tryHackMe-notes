## Cryptography Basics
Exchanging keys for symmetric encryption is a widespread **use of asymmetric cryptography**. Asymmetric encryption is relatively slow compared to symmetric encryption; therefore, we rely on asymmetric encryption to negotiate and agree on symmetric encryption ciphers and keys.

- **XOR** 
	- XOR compares two bits and returns 1 if the bits are different and 0 if they are the same
	- 0 ⊕ 0 = 0, 0 ⊕ 1 = 1, 1 ⊕ 0 = 1, and 1 ⊕ 1 = 0.
	- Consider the binary values P and K, where P is the plaintext, and K is the secret key. The ciphertext is C = P ⊕ K.
	- If we know C and K, we can recover P. We start with C ⊕ K = (P ⊕ K) ⊕ K. But we know that (P ⊕ K) ⊕ K = P ⊕ (K ⊕ K) because XOR is associative. Furthermore, we know that K ⊕ K = 0; consequently, (P ⊕ K) ⊕ K = P ⊕ (K ⊕ K) = P ⊕ 0 = P.
	- In practice, it is more complicated as we need a secret key as long as the plaintext.
- **Modulo**
	- 23%7 = 2 because 23 divided by 7 is 3 with a remainder of 2, i.e., 23 = 3 × 7 + 2
	- An important thing to remember about modulo is that it’s not reversible. If we are given the equation x%5 = 4, infinite values of x would satisfy this equation.
	- The modulo operation always returns a non-negative result less than the divisor. This means that for any integer a and positive integer n, the result of a%n will always be in the range 0 to n − 1.
- **RSA**
	1.  Bob chooses two prime numbers: _p_ = 157 and _q_ = 199. He calculates _n_ = _p_ × _q_ = 31243.
	2.  With _ϕ_(_n_) = _n_ − _p_ − _q_ + 1 = 31243 − 157 − 199 + 1 = 30888, Bob selects _e_ = 163 such that _e_ is relatively prime to _ϕ_(_n_); moreover, he selects _d_ = 379, where _e_ × _d_ = 1 mod _ϕ_(_n_), i.e., _e_ × _d_ = 163 × 379 = 61777 and 61777 mod 30888 = 1. The public key is (_n_,_e_), i.e., (31243,163) and the private key is $(n,d), i.e., (31243,379).
	3.  Let’s say that the value they want to encrypt is _x_ = 13, then Alice would calculate and send _y_ = _x__e_ mod _n_ = 13163 mod 31243 = 16341.
	4.  Bob will decrypt the received value by calculating _x_ = _y__d_ mod _n_ = 16341379 mod 31243 = 13. This way, Bob recovers the value that Alice sent.
	- You need to know the main variables for RSA in CTFs: p, q, m, n, e, d, and c. As per our numerical example:
		- p and q are large prime numbers
		-   n is the product of p and q
		- The public key is n and e
		- The private key is n and d
		- m is used to represent the original message, i.e., plaintext
		- c represents the encrypted text, i.e., ciphertext
- **Diffie Hellman**
- 

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwMDMwOTg0OTcsNjAxMjE4NDk5LDM1MD
E3MTY1N119
-->