# EX-NO-9-RSA-Algorithm

## AIM:
To Implement RSA Encryption Algorithm in Cryptography

## Algorithm:

STEP-1: Design of RSA Algorithm  
The RSA algorithm is based on the mathematical difficulty of factoring the product of two large prime numbers. It involves generating a public and private key pair, where the public key is used for encryption, and the private key is used for decryption.

STEP-2: Implementation in Python or C 
This algorithm can be implemented in languages like Python or C by performing large integer calculations for key generation, encryption, and decryption, utilizing libraries for modular arithmetic if necessary.

STEP-3: Algorithm Description  

1. Key Generation:
   - Select two large prime numbers \( p \) and \( q \).
   - Calculate \( n = p \times q \), which will be used as the modulus.
   - Compute the totient \( \phi(n) = (p - 1)(q - 1) \).
   - Choose a public exponent \( e \) such that \( e \) is coprime with \( \phi(n) \).
   - Compute the private key \( d \), which is the modular inverse of \( e \) mod \( \phi(n) \).

2. Encryption:
   - Convert the plaintext message \( M \) into a numerical form \( m \) (such that \( 0 \le m < n \)).
   - Compute the ciphertext \( c \) using the formula: \( c = m^e \mod n \).

3. Decryption:
   - Use the private key \( d \) to recover \( m \) from \( c \) using: \( m = c^d \mod n \).
   - Convert \( m \) back into the original message \( M \).

STEP-4: Mathematical Representation  
- Encryption: \( E(m) = m^e \mod n \)
- Decryption: \( D(c) = c^d \mod n \)

STEP-5: Security Foundation  
The security of RSA relies on the difficulty of factoring large numbers; thus, choosing sufficiently large prime numbers for \( p \) and \( q \) is crucial for security.

## Program:

```
#include <stdio.h>
#include <string.h>

long long power(long long a, long long b, long long mod)
{
    long long result = 1;
    while(b > 0)
    {
        if(b % 2 == 1)
        {
            result = (result * a) % mod;
        }
        a = (a * a) % mod;
        b = b / 2;
    }
    return result;
}

int main()
{
    int p = 17, q = 11;
    int n = p * q;
    int e = 7;
    int d = 23;
    char name[50];
    printf("RSA Algorithm\n");
    printf("\nEnter Text : ");
    scanf("%s", name);
    int len = strlen(name);
    long long encrypted[50];
    printf("\nEncrypted Message : ");
    for(int i = 0; i < len; i++)
    {
        encrypted[i] = power(name[i], e, n);
        printf("%lld ", encrypted[i]);
    }
    printf("\nDecrypted Message : ");
    for(int i = 0; i < len; i++)
    {
        char ch = power(encrypted[i], d, n);
        printf("%c", ch);
    }
    return 0;
}
```

## Output:

<img width="1914" height="896" alt="ex9op" src="https://github.com/user-attachments/assets/51df269a-c13d-4015-9769-8d6f9714e420" />

## Result:
Thus, the implementation of RSA Encryption Algorithm in Cryptography had been executed successfully.
