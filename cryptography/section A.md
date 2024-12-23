a) Euler's Totient Function

The Euler's Totient Function, ϕ(n)ϕ(n), is the number of integers less than nn that are relatively prime to nn. If nn is a positive integer, ϕ(n)ϕ(n) counts the numbers kk such that 1≤k≤n1≤k≤n and gcd(n,k)=1gcd(n,k)=1.

Example:
For n=9n=9, the integers less than 9 are 1,2,3,4,5,6,7,81,2,3,4,5,6,7,8.
The numbers relatively prime to 9 are 1,2,4,5,7,81,2,4,5,7,8, so ϕ(9)=6ϕ(9)=6.
b) GCD of 2740 and 1760

Using the Euclidean Algorithm:

    2740mod  1760=9802740mod1760=980
    1760mod  980=7801760mod980=780
    980mod  780=200980mod780=200
    780mod  200=180780mod200=180
    200mod  180=20200mod180=20
    180mod  20=0180mod20=0

Thus, gcd(2740,1760)=20gcd(2740,1760)=20.
c) Weak Collision Resistance in Hash Functions

A hash function h(x)h(x) is weakly collision-resistant if it is computationally infeasible to find a different input x′x′ such that h(x)=h(x′)h(x)=h(x′), given xx.

d) Shannon's Theory of Confusion and Diffusion
    Confusion: The relationship between the ciphertext and the key should be complex, making it difficult for an attacker to deduce the key.
    Diffusion: The plaintext statistics should spread over the ciphertext so that a small change in the plaintext causes widespread changes in the ciphertext.

e) Triple DES

Triple DES (3DES) is an encryption algorithm that applies the DES cipher three times to each data block. It uses three keys K1,K2,K1​,K2​, and K3K3​ as follows:
Ciphertext=EK3(DK2(EK1(Plaintext)))Ciphertext=EK3​​(DK2​​(EK1​​(Plaintext)))
f) Symmetric vs. Asymmetric Key Cryptography

  Symmetric: Uses a single key for encryption and decryption (e.g., AES, DES). It is faster but requires secure key distribution.
    Asymmetric: Uses a public key for encryption and a private key for decryption (e.g., RSA, ECC). It is more secure for key exchange but slower.

g) Padding in SHA-1

SHA-1 appends padding bits such that the total message length becomes a multiple of 512 bits. Padding consists of a '1' bit followed by '0' bits, ending with a 64-bit representation of the original message length.
h) Avalanche Effect

The avalanche effect is a desirable property in cryptography where a small change in the input (e.g., flipping a single bit) produces a significant change in the output, ensuring unpredictability.
i) Classical vs. Modern Cryptography

    Classical Cryptography: Uses techniques like substitution and transposition. Example: Caesar cipher.
    Modern Cryptography: Employs mathematical algorithms and computational hardness assumptions. Example: RSA, AES.

j) Value of ϕ(49)ϕ(49)

Since 49=7249=72 and ϕ(pk)=pk−pk−1ϕ(pk)=pk−pk−1 for prime pp:
ϕ(49)=49−7=42ϕ(49)=49−7=42
