Kerberos Version 4 and Its Differences with Version 5
Kerberos Version 4 (KRB4)

Kerberos is a network authentication protocol designed to provide strong authentication for client-server applications.

Key Features of Version 4:

    Trusted Third Party (TTP): Relies on a Key Distribution Center (KDC) to mediate between clients and services.
    Tickets: Users obtain a ticket-granting ticket (TGT) from the KDC, which is used to request service-specific tickets.
    Symmetric Encryption: Utilizes symmetric cryptography (e.g., DES) for communication.
    Time Synchronization: Requires synchronized clocks to prevent replay attacks.
    Architecture:
        Authentication Server (AS): Issues TGT.
        Ticket Granting Server (TGS): Issues service tickets.
    Limitation: Supports only IPv4 and lacks internationalization.

Differences Between Kerberos Version 4 and Version 5
Feature	Kerberos Version 4	Kerberos Version 5
Protocol Support	Only IPv4	Both IPv4 and IPv6
Encryption Algorithms	DES only	Multiple algorithms (e.g., AES)
Replay Protection	Time-based tickets	Nonces and improved timestamping
Ticket Lifetime	Fixed	Adjustable
Cross-Realm Authentication	Limited	More robust
Internationalization	Lacks support	Supports Unicode
Extensions	Not extensible	Extensible


a ii) Man-in-the-Middle Attack Over Diffie-Hellman
Description

The Diffie-Hellman key exchange is vulnerable to a man-in-the-middle (MITM) attack when no authentication is used. In this attack:

    The attacker intercepts the communication between two parties (Alice and Bob).
    The attacker establishes two separate key exchanges, one with Alice and one with Bob, using their public keys.
    The attacker decrypts, modifies, and re-encrypts the data transparently.

Example

    Alice sends her public key gamod  pgamodp to Bob.
    The attacker intercepts it and sends gemod  pgemodp (attacker’s key) to Bob.
    Bob sends his public key gbmod  pgbmodp to Alice, but the attacker intercepts and replaces it with gemod  pgemodp.
    Both Alice and Bob believe they have securely exchanged keys, but the attacker controls the session.

Solution

Authentication methods like digital signatures or certificates can mitigate this risk.


b i) Four Modes of Operation of a Block Cipher

    Electronic Codebook (ECB)
        Each block is encrypted independently.
        Simple but vulnerable to patterns in plaintext.
        Diagram: Plaintext → Encryption → Ciphertext (per block).

    Cipher Block Chaining (CBC)
        Each plaintext block is XORed with the previous ciphertext block before encryption.
        Requires an initialization vector (IV).
        Diagram: Ci=E(Pi⊕Ci−1)Ci​=E(Pi​⊕Ci−1​).

    Cipher Feedback (CFB)
        Converts block ciphers into stream ciphers.
        XORs plaintext with the encrypted output of the previous ciphertext.
        Diagram: Ci=Pi⊕E(Ci−1)Ci​=Pi​⊕E(Ci−1​).

    Output Feedback (OFB)
        Similar to CFB but does not use the ciphertext in feedback.
        Ensures that encryption errors do not propagate.
        Diagram: Ci=Pi⊕OiCi​=Pi​⊕Oi​, where Oi=E(Oi−1)Oi​=E(Oi−1​).

b ii) SSL and TLS
SSL Overview

    Secure Sockets Layer (SSL) ensures encrypted communication between web servers and clients.
    Operates at the transport layer.
    Components:
        Handshake Layer: Authentication and session establishment.
        Record Layer: Data transmission using encryption.
        Change Cipher Spec Layer: Secures the ongoing session.

Differences Between SSL and TLS
Feature	SSL	TLS
Security	Less secure	More secure
Protocol Version	SSL 2.0, 3.0	TLS 1.0, 1.1, 1.2, 1.3
Algorithms	Fewer supported	Modern algorithms
Vulnerabilities	POODLE	Improved protection


c i) Digital Signature and ElGamal Technique
Digital Signature

A digital signature is a cryptographic technique that verifies the authenticity and integrity of a message.

Diagram:

    Hash the message.
    Encrypt the hash using the sender’s private key.
    Send the message and signature to the receiver.

ElGamal Digital Signature

    Generate keys: Private key xx, public key y=gxmod  py=gxmodp.
    Signing:
        Generate a random kk such that gcd(k,p−1)=1gcd(k,p−1)=1.
        Compute r=gkmod  pr=gkmodp.
        Compute s=k−1(H(m)−xr)mod  (p−1)s=k−1(H(m)−xr)mod(p−1).
        Signature: (r,s)(r,s).
    Verification:
        Check gH(m)≡yrrsmod  pgH(m)≡yrrsmodp.

Correctness

The verification equation holds due to modular arithmetic and properties of g.


c (ii)

Hash Function

A hash function is a cryptographic algorithm that maps input data of arbitrary size to a fixed-size hash value. It is widely used for data integrity verification and digital signatures.
Key Properties of Hash Functions:

    Deterministic: The same input always produces the same hash.
    Fast Computation: Efficient to compute for any input size.
    Pre-image Resistance: Hard to find the input given a hash value.
    Collision Resistance: Hard to find two different inputs that produce the same hash.
    Avalanche Effect: Small changes in the input significantly change the hash output.

SHA-1 (Secure Hash Algorithm 1)
Overview

    Produces a 160-bit hash value.
    Designed by the NSA and standardized by NIST.
    Processes messages in blocks of 512 bits.

Steps of SHA-1

    Padding:
        Add a single '1' bit to the message.
        Add '0' bits until the length of the message (in bits) is 448 modulo 512.
        Append the original message length as a 64-bit big-endian integer.

    Block Division:
        Divide the padded message into 512-bit blocks.

    Initialization:
        Initialize five 32-bit hash values: H0=0x67452301H0​=0x67452301, H1=0xEFCDAB89H1​=0xEFCDAB89, H2=0x98BADCFEH2​=0x98BADCFE, H3=0x10325476H3​=0x10325476, H4=0xC3D2E1F0H4​=0xC3D2E1F0.

    Processing:
        For each block, divide it into 16 words W[0]W[0] to W[15]W[15] of 32 bits each.
        Extend W[i]W[i] to W[79]W[79] using the formula:
        W[i]=(W[i−3]⊕W[i−8]⊕W[i−14]⊕W[i−16])≪1W[i]=(W[i−3]⊕W[i−8]⊕W[i−14]⊕W[i−16])≪1
        (≪1≪1 is a 1-bit left circular shift).

    Round Function:

        Perform 80 rounds, grouped into four stages of 20 rounds each.

        Each stage uses a different constant KK and a non-linear function FF:
            Rounds 0–19: F(B,C,D)=(B∧C)∨(¬B∧D)F(B,C,D)=(B∧C)∨(¬B∧D), K=0x5A827999K=0x5A827999.
            Rounds 20–39: F(B,C,D)=B⊕C⊕DF(B,C,D)=B⊕C⊕D, K=0x6ED9EBA1K=0x6ED9EBA1.
            Rounds 40–59: F(B,C,D)=(B∧C)∨(B∧D)∨(C∧D)F(B,C,D)=(B∧C)∨(B∧D)∨(C∧D), K=0x8F1BBCDCK=0x8F1BBCDC.
            Rounds 60–79: F(B,C,D)=B⊕C⊕DF(B,C,D)=B⊕C⊕D, K=0xCA62C1D6K=0xCA62C1D6.

        Update hash values using:
        TEMP=(A≪5)+F(B,C,D)+E+W[t]+K
        TEMP=(A≪5)+F(B,C,D)+E+W[t]+K

        Update:
        E=D,D=C,C=B≪30,B=A,A=TEMPE=D,D=C,C=B≪30,B=A,A=TEMP.

    Final Hash:

        Add the output of the last block to the initial hash values:
        H0,H1,H2,H3,H4
        H0​,H1​,H2​,H3​,H4​

        Concatenate H0,H1,H2,H3,H4H0​,H1​,H2​,H3​,H4​ to produce the 160-bit hash.

Block Diagram of SHA-1

The block diagram includes:

    Input message processing: Padding and block division.
    Initialization of hash values.
    Iterative processing: 80 rounds of the round function.
    Output hash: 160-bit value.

Comparison of SHA-1 and MD5
Feature	MD5	SHA-1
Hash Length	128 bits	160 bits
Speed	Faster	Slower
Security	Vulnerable to collisions	More secure but still weak
Block Size	512 bits	512 bits
Rounds	64	80
Current Use	Deprecated for security	Deprecated for security
Conclusion

SHA-1 offers better security than MD5 but is considered obsolete due to collision vulnerabilities. Modern cryptographic standards prefer algorithms like SHA-256.
