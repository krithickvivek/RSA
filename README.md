# RSA-EXP

## AIM: 
To implement the RSA algorithm for encryption and decryption in C using string input.

## ALGORITHM:

1. Choose two prime numbers and calculate the modulus n.

2. Generate public and private keys based on the chosen prime numbers.

3. Encrypt the plaintext by converting characters to their ASCII values and performing encryption using the public key.

4. Decrypt the ciphertext using the private key to retrieve the original plaintext.


## PROGRAM:
```
#include <stdio.h>
#include <string.h>
#include <math.h>

// Function to find GCD
int gcd(int a, int b) {
    while (b != 0) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

// Function to perform modular exponentiation (base^exp % mod)
int modExp(int base, int exp, int mod) {
    int result = 1;
    base = base % mod;
    while (exp > 0) {
        if (exp % 2 == 1) {
            result = (result * base) % mod;
        }
        exp = exp >> 1;
        base = (base * base) % mod;
    }
    return result;
}

int main() {
    int p = 61, q = 53;  // Example prime numbers
    int n = p * q;
    int phi = (p - 1) * (q - 1);
    int e = 17;  // Public key exponent
    int d = 2753;  // Private key exponent (calculated separately)

    char plaintext[100], ciphertext[100];
    int encrypted[100], decrypted[100];

    // Input plaintext
    printf("Enter the plaintext: ");
    scanf("%s", plaintext);

    // Encryption
    int len = strlen(plaintext);
    printf("Encrypted Message (ASCII values): ");
    for (int i = 0; i < len; i++) {
        encrypted[i] = modExp(plaintext[i], e, n);
        printf("%d ", encrypted[i]);
    }
    printf("\n");

    // Decryption
    printf("Decrypted Message: ");
    for (int i = 0; i < len; i++) {
        decrypted[i] = modExp(encrypted[i], d, n);
        printf("%c", decrypted[i]);
    }
    printf("\n");

    return 0;
}

```
## OUTPUT:

![image](https://github.com/user-attachments/assets/2437c954-53b7-4e36-983b-5e8bff5877a0)


## RESULT:
The program for the RSA algorithm is executed successfully, demonstrating both encryption and decryption.



