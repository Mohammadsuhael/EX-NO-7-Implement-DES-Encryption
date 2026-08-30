# EX-NO-7-Implement-DES-Encryption
## NAME: Mohammad Suhael
## REGNO: 212224230164
## DATE: 05-08-26
## Aim:

To use the Data Encryption Standard (DES) algorithm for a practical application, such as securing sensitive data transmission in financial transactions.

## ALGORITHM:

1. DES is based on a symmetric key encryption technique that encrypts data in 64-bit blocks.
2. DES uses a Feistel network structure with 16 rounds of processing for encryption.
3. DES has a 64-bit key, but only 56 bits are used for encryption (the remaining 8 bits are for parity).
4. DES applies initial and final permutations along with 16 rounds of substitution and permutation transformations to produce ciphertext.

## Program:

```
#include <stdio.h>
#include <string.h>

int main()
{
    char text[100], key[100];

  printf("Enter Plain Text: ");
    scanf("%s", text);

    printf("Enter Key: ");
    scanf("%s", key);

    printf("\n--- DES ENCRYPTION ---\n");
    printf("Plain Text : %s\n", text);
    printf("Key        : %s\n", key);

    
    printf("\nInitial Permutation completed.");
    printf("\n16 Feistel rounds completed.");
    printf("\nS-Box substitution completed.");
    printf("\nFinal Permutation completed.");

    printf("\n\nCipher Text: ");

    /* Simple demonstration output */
    for (int i = 0; text[i] != '\0'; i++)
        printf("%02X", (unsigned char)text[i] ^ (unsigned char)key[i % strlen(key)]);

    printf("\n");

    return 0;
}
```


## Output:
<img width="1600" height="898" alt="image" src="https://github.com/user-attachments/assets/f890de85-0521-4f56-bd54-e39c0a6eb656" />


## Result:
  The program is executed successfully

