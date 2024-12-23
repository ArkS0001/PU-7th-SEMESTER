E-mail Security and Pretty Good Privacy (PGP)
E-mail Security

E-mail security ensures that communication over email remains confidential, authentic, and intact. Common threats include phishing, spam, malware, and data breaches. E-mail security mechanisms include encryption, digital signatures, and secure protocols like SSL/TLS.
Pretty Good Privacy (PGP)

PGP is a cryptographic method to secure emails through encryption and digital signatures. It combines:

    Symmetric Key Encryption: For encrypting the message body.
    Public Key Encryption: For encrypting the symmetric key using the recipient's public key.
    Hashing: For creating a digital signature to verify message integrity and authenticity.

Steps in PGP Encryption:

    The message is compressed to save space and reduce transmission time.
    A random session key is generated and used to encrypt the compressed message using symmetric encryption (e.g., AES).
    The session key is encrypted using the recipient's public key.
    Both the encrypted message and encrypted session key are sent to the recipient.

Steps in PGP Decryption:

    The recipient uses their private key to decrypt the session key.
    The session key is used to decrypt the message.
    The original message is decompressed.

PGP provides confidentiality, integrity, authentication, and non-repudiation.


a) ii) Security Association (SA) in IPSec and ISAKMP Protocol
Security Association (SA)

    SA is a unidirectional logical connection between two entities in IPSec, used to define the parameters of secured communication.

    SA includes:
        Security Parameters Index (SPI): A unique identifier for the SA.
        IPSec Protocol: AH (Authentication Header) or ESP (Encapsulating Security Payload).
        Encryption/Authentication Algorithms: Specifies the algorithms used.

    SA Management: Typically managed by the ISAKMP protocol.

ISAKMP (Internet Security Association and Key Management Protocol)

    A framework for key exchange and SA negotiation in IPSec.
    Ensures secure communication by:
        Establishing, modifying, and deleting SAs.
        Handling authentication and key exchange.
        Supporting multiple key exchange protocols (e.g., IKE - Internet Key Exchange).


-----------------------------------------------------------------------------------

To decrypt the ciphertext "FKMFIO" using the Hill cipher with the key matrix:
K=[2336]
K=[23​36​]

we follow these steps:
1. Represent the ciphertext as numerical values

Convert each letter to its numerical equivalent (A=0, B=1, ..., Z=25):

    F → 5
    K → 10
    M → 12
    F → 5
    I → 8
    O → 14

Thus, the ciphertext as a sequence of numbers:
5,10,12,5,8,145,10,12,5,8,14
2. Pair the ciphertext numbers

Group the numbers into pairs (since the key is a 2×22×2 matrix):
Pairs: [510],[125],[814].
Pairs: [510​],[125​],[814​].
3. Calculate the inverse of the key matrix modulo 26

To decrypt, we need the inverse of the key matrix KK modulo 26.
K=[2336]
K=[23​36​]
Step a: Find the determinant of KK modulo 26

The determinant is:
det(K)=(2×6)−(3×3)=12−9=3.
det(K)=(2×6)−(3×3)=12−9=3.

Modulo 26:
det(K)mod  26=3.
det(K)mod26=3.
Step b: Find the modular multiplicative inverse of the determinant

We need an integer dd such that:
3⋅d≡1(mod26).
3⋅d≡1(mod26).

The modular inverse of 3 modulo 26 is 99 because:
3⋅9=27≡1(mod26).
3⋅9=27≡1(mod26).
Step c: Compute the adjugate of KK

The adjugate (matrix of cofactors) of KK is:
adj(K)=[6−3−32].
adj(K)=[6−3​−32​].

Modulo 26:
adj(K)=[623232].
adj(K)=[623​232​].
Step d: Compute the inverse matrix

The inverse matrix is:
K−1=(det−1⋅adj(K))mod  26.
K−1=(det−1⋅adj(K))mod26.

Substitute:
K−1=(9⋅[623232])mod  26.
K−1=(9⋅[623​232​])mod26.

Multiply:
K−1=[5420720718]mod  26=[2252518].
K−1=[54207​20718​]mod26=[225​2518​].

Thus:
K−1=[2252518].
K−1=[225​2518​].
4. Decrypt the ciphertext

For each pair [x1x2][x1​x2​​], multiply by K−1K−1 modulo 26:
[p1p2]=K−1⋅[x1x2]mod  26.
[p1​p2​​]=K−1⋅[x1​x2​​]mod26.
**Decrypt first pair: (

\begin{bmatrix} 5 \ 10 \end{bmatrix} )**
[p1p2]=[2252518]⋅[510]mod  26.
[p1​p2​​]=[225​2518​]⋅[510​]mod26.

Calculate:
p1=(2⋅5+25⋅10)mod  26=(10+250)mod  26=260mod  26=0.
p1​=(2⋅5+25⋅10)mod26=(10+250)mod26=260mod26=0.
p2=(25⋅5+18⋅10)mod  26=(125+180)mod  26=305mod  26=19.
p2​=(25⋅5+18⋅10)mod26=(125+180)mod26=305mod26=19.

Decrypted pair:
[019]
[019​]

Corresponds to letters: A T.
Repeat for the remaining pairs:

    [125][125​] → C O
    [814][814​] → M S

5. Final decrypted message

The plaintext is:
"ATCOMS".


---------------------------------------------------------

AES Encryption/Decryption Architecture
Diagram of AES Architecture

The AES (Advanced Encryption Standard) architecture consists of several stages applied iteratively over multiple rounds. The diagram can be described as follows:
```
+-------------------+
| Input Plaintext   |
+-------------------+
         |
  +---------------+
  | AddRoundKey   |
  +---------------+
         |
  +----------------+       +----------------+
  | SubBytes       | ----> | InvSubBytes    |
  +----------------+       +----------------+
         |
  +----------------+       +----------------+
  | ShiftRows      | ----> | InvShiftRows   |
  +----------------+       +----------------+
         |
  +----------------+       +----------------+
  | MixColumns     | ----> | InvMixColumns  |
  +----------------+       +----------------+
         |
  +---------------+
  | AddRoundKey   |
  +---------------+
         |
      Repeat (Nr rounds)
         |
  +-------------------+
  | Ciphertext Output |
  +-------------------+
```

Stages in AES Algorithm

    Key Expansion:
        The input key is expanded into multiple round keys using the AES key schedule.
        The number of round keys depends on the key size (128, 192, or 256 bits).

    Initial Round:
        AddRoundKey: XOR the plaintext block with the first round key.

    Main Rounds (Repeated Nr times, where Nr = 10 for 128-bit key):
        SubBytes:
            A non-linear substitution step where each byte is replaced with another byte from a fixed S-Box (Substitution Box).
        ShiftRows:
            A permutation step where rows of the state matrix are shifted cyclically.
        MixColumns:
            A linear transformation applied to each column of the state matrix, mixing the data.
        AddRoundKey:
            XOR the state matrix with the current round key.

    Final Round:
        Similar to the main rounds but omits the MixColumns step.

    Ciphertext Output:
        The resulting state after the final round is the ciphertext.

Chinese Remainder Theorem (CRT)
Theorem

The Chinese Remainder Theorem states that if xx satisfies a set of congruences:
x≡a1(modm1),x≡a2(modm2),…,x≡ak(modmk)
x≡a1​(modm1​),x≡a2​(modm2​),…,x≡ak​(modmk​)

and m1,m2,…,mkm1​,m2​,…,mk​ are pairwise coprime, there exists a unique solution modulo M=m1⋅m2⋅⋯⋅mkM=m1​⋅m2​⋅⋯⋅mk​.
Problem

Solve for xx such that:
x≡2(mod5),x≡3(mod7),x≡10(mod11).
x≡2(mod5),x≡3(mod7),x≡10(mod11).
Solution

    Determine MM:
    M=5⋅7⋅11=385.
    M=5⋅7⋅11=385.

    Compute individual MiMi​ values:
    M1=Mm1=3855=77,M2=Mm2=3857=55,M3=Mm3=38511=35.
    M1​=m1​M​=5385​=77,M2​=m2​M​=7385​=55,M3​=m3​M​=11385​=35.

    Compute modular inverses of MiMi​ modulo mimi​: Find M1−1mod  5M1−1​mod5, M2−1mod  7M2−1​mod7, and M3−1mod  11M3−1​mod11:
        77mod  5=277mod5=2, solve 2x≡1(mod5)2x≡1(mod5): x=3x=3.
        55mod  7=655mod7=6, solve 6x≡1(mod7)6x≡1(mod7): x=6x=6.
        35mod  11=235mod11=2, solve 2x≡1(mod11)2x≡1(mod11): x=6x=6.

    Thus:
    M1−1=3,M2−1=6,M3−1=6.
    M1−1​=3,M2−1​=6,M3−1​=6.

    Calculate xx using CRT formula:
    x=∑i=13ai⋅Mi⋅Mi−1mod  M
    x=i=1∑3​ai​⋅Mi​⋅Mi−1​modM

    Substitute:
    x=(2⋅77⋅3)+(3⋅55⋅6)+(10⋅35⋅6)mod  385.
    x=(2⋅77⋅3)+(3⋅55⋅6)+(10⋅35⋅6)mod385.

    Simplify each term:
        2⋅77⋅3=4622⋅77⋅3=462,
        3⋅55⋅6=9903⋅55⋅6=990,
        10⋅35⋅6=210010⋅35⋅6=2100.

    Add and take modulo 385385:
    x=(462+990+2100)mod  385=3552mod  385=47.
    x=(462+990+2100)mod385=3552mod385=47.



Firewalls: Definition, Working, and Types
Definition

A firewall is a network security system designed to monitor and control incoming and outgoing network traffic based on predefined security rules. It acts as a barrier between a trusted internal network and untrusted external networks, such as the internet, to prevent unauthorized access.
Working Process

    Packet Filtering:
        Examines data packets against a set of filters.
        Allows or blocks packets based on source/destination IP, protocol, or port numbers.

    Stateful Inspection:
        Monitors the state of active connections and determines whether a packet is part of an existing connection or a new one.
        Ensures packets are allowed only if part of a legitimate session.

    Proxy Service:
        Intercepts all requests and responses between two endpoints.
        Acts as a mediator for connections between internal and external networks.

    Deep Packet Inspection (DPI):
        Inspects packet contents, analyzing payload data for malicious content, such as malware signatures or intrusion patterns.

Types of Firewalls

    Packet-Filtering Firewall:
        Analyzes network packets and permits or denies them based on rules.
        Simple and fast but lacks advanced features.

    Stateful Inspection Firewall:
        Tracks the state of active connections.
        Provides better security than packet filtering.

    Proxy Firewall:
        Works at the application layer.
        Acts as an intermediary between client and server for added security.

    Next-Generation Firewall (NGFW):
        Combines traditional firewall features with additional capabilities like intrusion prevention, DPI, and application awareness.

    Network Address Translation (NAT) Firewall:
        Hides private IP addresses of devices in a network by translating them to a public IP address.

    Web Application Firewall (WAF):
        Protects web applications by filtering and monitoring HTTP traffic.
        Guards against attacks like SQL injection and cross-site scripting.

(d.ii) Viruses and Intrusion Detection Systems (IDS)
Viruses: Definition, Phases, and Types
Definition

A virus is a malicious software program designed to replicate itself and spread from one device to another, often damaging systems, corrupting files, or stealing information.
Phases of a Virus

    Dormant Phase:
        The virus remains inactive until triggered by an event (e.g., a date or program execution).

    Propagation Phase:
        The virus replicates itself and spreads to other files or systems.

    Triggering Phase:
        The virus activates, preparing to execute its malicious payload.

    Execution Phase:
        The virus performs its intended malicious actions, such as corrupting files or stealing data.

Types of Viruses

    File Infectors:
        Attach to executable files and activate when the file is run.

    Boot Sector Viruses:
        Infect the boot sector of a hard drive or removable media, activating during system startup.

    Macro Viruses:
        Target software macros in programs like Microsoft Word or Excel.

    Polymorphic Viruses:
        Change their code to evade detection by antivirus software.

    Metamorphic Viruses:
        Rewrite their code entirely, making detection more difficult.

Structures of Viruses

    Encrypted Viruses:
        Use encryption to hide their payload.

    Stealth Viruses:
        Mask themselves to avoid detection.

    Multipartite Viruses:
        Infect multiple parts of a system, such as boot sectors and executable files.

Intrusion Detection System (IDS)
Definition

An IDS is a network security tool designed to detect and alert administrators about suspicious or malicious activity within a network or system.
Types of IDS

    Network-Based IDS (NIDS):
        Monitors network traffic for suspicious activity.
        Works at the network layer.

    Host-Based IDS (HIDS):
        Monitors system files and activities on individual devices.

    Signature-Based IDS:
        Detects threats by matching patterns against known attack signatures.

    Anomaly-Based IDS:
        Identifies unusual behavior by establishing a baseline of normal activity and flagging deviations.

Working Process of IDS

    Data Collection:
        Gathers data from network traffic, system logs, or application activity.

    Analysis:
        Compares the collected data against known attack signatures or baseline behaviors.

    Alert Generation:
        Generates alerts when suspicious activity is detected.

    Response:
        Can trigger automated actions like blocking IP addresses or shutting down services to mitigate threats.


---------------------------------

Elliptic Curve Cryptography (ECC)
Demonstration

Elliptic Curve Cryptography (ECC) is a public-key cryptography technique based on the mathematical properties of elliptic curves. It provides the same level of security as traditional cryptographic systems like RSA but with smaller key sizes, making it more efficient.
Elliptic Curve Equation

The equation for an elliptic curve is:
y2=x3+ax+bmod  p
y2=x3+ax+bmodp

where:

    aa and bb are constants.
    pp is a prime number defining the finite field GF(p)GF(p).

Key Concepts

    Point Addition:
        Given two points PP and QQ on the curve, their sum R=P+QR=P+Q is also on the curve.

    Scalar Multiplication:
        Multiplying a point PP by a scalar kk (kPkP) generates another point on the curve. This forms the basis of ECC encryption.

Uses in Encryption and Authentication

    Encryption:
        ECC is used in protocols like ECDH (Elliptic Curve Diffie-Hellman) for secure key exchange.

    Authentication:
        ECC is utilized in digital signatures (e.g., ECDSA) to verify the authenticity of messages or documents.

Advantages

    Smaller Key Sizes: ECC provides equivalent security with much smaller key sizes compared to RSA.
    Efficiency: Reduced computational overhead makes ECC ideal for resource-constrained devices.
    Security: The discrete logarithm problem on elliptic curves is harder to solve than on traditional systems.

(e.ii) Explanation of Topics
1. S/MIME (Secure/Multipurpose Internet Mail Extensions)

S/MIME is a standard for secure email communication that provides:

    Authentication: Ensures the sender is who they claim to be.
    Integrity: Ensures the message is not tampered with.
    Encryption: Protects the message content from unauthorized access.

Working:

    Uses asymmetric cryptography to encrypt emails.
    Digital signatures verify authenticity.

2. GF(p) (Galois Field of Prime Order)

    A Galois Field GF(p)GF(p) is a finite field consisting of pp elements, where pp is a prime number.
    Operations (addition, subtraction, multiplication, division) are performed modulo pp.
    Usage: Widely used in cryptography for modular arithmetic in RSA, ECC, and AES.

3. Steganography

    Definition: The practice of hiding secret data within a non-secret medium, such as images, videos, or text.
    Types:
        Text Steganography: Hiding data in text.
        Image Steganography: Embedding data in image pixels.
        Audio Steganography: Concealing data in audio files.
    Applications: Secure communication, watermarking.

4. Known Ciphertext Attack & Known Plaintext Attack

    Known Ciphertext Attack:
        The attacker only has access to ciphertext and attempts to deduce the plaintext or key.
        Example: Brute force.

    Known Plaintext Attack:
        The attacker has access to both plaintext and ciphertext pairs and uses this information to discover the encryption key.

5. Non-Repudiation

    Definition: Ensures that a sender cannot deny the authenticity of their message.
    Mechanism: Achieved through digital signatures, providing proof of origin and integrity.

6. RSA Algorithm

Definition: RSA is an asymmetric cryptographic algorithm used for secure data transmission.

Key Steps:

    Key Generation:
        Choose two large prime numbers pp and qq.
        Compute n=pqn=pq and ϕ(n)=(p−1)(q−1)ϕ(n)=(p−1)(q−1).
        Select public key ee such that 1<e<ϕ(n)1<e<ϕ(n) and gcd(e,ϕ(n))=1gcd(e,ϕ(n))=1.
        Compute private key dd such that ed≡1mod  ϕ(n)ed≡1modϕ(n).

    Encryption:
        Ciphertext C=Memod  nC=Memodn, where MM is the plaintext.

    Decryption:
        Plaintext M=Cdmod  nM=Cdmodn.

Advantages:

    Secure against brute force with sufficiently large keys.
    Widely used for digital signatures and key exchange.

--------------------------------------
