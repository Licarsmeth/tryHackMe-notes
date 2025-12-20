## Cryptography Basics
Exchanging keys for symmetric encryption is a widespread **use of asymmetric cryptography**. Asymmetric encryption is relatively slow compared to symmetric encryption; therefore, we rely on asymmetric encryption to negotiate and agree on symmetric encryption ciphers and keys. 
Diffie Hellman is also an alternative. 

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
	- RSA is a public-key encryption algorithm that enables secure data transmission over insecure channels. With an insecure channel, we expect adversaries to eavesdrop on it.
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
- **Diffie Hellman (Key Exchange)**	
		1.  Alice and Bob agree on the **public variables**: a large prime number _p_ and a generator _g_, where 0 < _g_ < _p_. These values will be disclosed publicly over the communication channel. Although insecurely small, we will choose _p_ = 29 and _g_ = 3 to simplify our calculations.
		2.  Each party chooses a private integer. As a numerical example, Alice chooses _a_ = 13, and Bob chooses _b_ = 15. Each of these values represents a **private key** and must not be disclosed.
		3. It is time for each party to calculate their **public key** using their private key from step 2 and the agreed-upon public variables from step 1. Alice calculates _A_ = _g__a_ mod _p_ = 313 mod 29 = 19 and Bob calculates _B_ = _g__b_ mod _p_ = 315 mod 29 = 26. These are the public keys.
		4. Alice and Bob send the keys to each other. Bob receives _A_ = _g__a_ mod _p_ = 19, i.e., Alice’s public key. And Alice receives _B_ = _g__b_ mod _p_ = 26, i.e., Bob’s public key. This step is called the **key exchange**.
		5. Alice and Bob can finally calculate the **shared secret** using the received public key and their own private key. Alice calculates _B__a_ mod _p_ = 2613 mod 29 = 10 and Bob calculates _A__b_ mod _p_ = 1915 mod 29 = 10. Both calculations yield the same result, _g__a__b_ mod _p_ = 10, the shared secret key.
	- Note on RSA and Diffie Hellman usage:
		- Diffie-Hellman Key Exchange is often used alongside RSA public key cryptography. Diffie-Hellman is used for key agreement, while RSA is used for digital signatures, key transport, and authentication, among many others. For instance, RSA helps prove the identity of the person you’re talking to via digital signing, as you can confirm based on their public key. This would prevent someone from attacking the connection with a man-in-the-middle attack against Alice by pretending to be Bob. In brief, Diffie-Hellman and RSA are incorporated into many security protocols and standards to provide a comprehensive security solution.
		1. Alice signs "p=23,g=5" with PRIVATE key 
		2. Bob verifies signature with Alice's PUBLIC key 
		3. Bob signs his public value B=19 with HIS PRIVATE key 
		4. Alice verifies Bob's signature
	This way, no MITM attacks are possible trying to impersonate them.
- **SSH**
	 1. Generate keypair (ONCE)
		 - `ssh-keygen -t ed25519`
		-  Creates: ~/.ssh/id_ed25519 (PRIVATE - NEVER SHARE) 
		-  Creates: ~/.ssh/id_ed25519.pub (PUBLIC - safe to share)  
	2. Copy public key to server
		- `ssh-copy-id user@server `
		- Adds your .pub to server's ~/.ssh/authorized_keys
	3. SSH login (automatic): 
		- `ssh user@server`
		- Client: Signs challenge with PRIVATE key # Server: Verifies signature with your PUBLIC key in authorized_keys # Result: Logged in - NO PASSWORD!

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI3NTkzNDA0NCwtMTc5ODEwMzM4NywxMj
I1MDE4ODEwLC0xNjQ4NzYzNzE3LDMxNzA2MDg2OSwtMTAwMzA5
ODQ5Nyw2MDEyMTg0OTksMzUwMTcxNjU3XX0=
-->