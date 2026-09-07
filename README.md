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
#include <stdint.h>

int IP[64] = {
58,50,42,34,26,18,10,2,60,52,44,36,28,20,12,4,
62,54,46,38,30,22,14,6,64,56,48,40,32,24,16,8,
57,49,41,33,25,17,9,1,59,51,43,35,27,19,11,3,
61,53,45,37,29,21,13,5,63,55,47,39,31,23,15,7
};

int FP[64] = {
40,8,48,16,56,24,64,32,39,7,47,15,55,23,63,31,
38,6,46,14,54,22,62,30,37,5,45,13,53,21,61,29,
36,4,44,12,52,20,60,28,35,3,43,11,51,19,59,27,
34,2,42,10,50,18,58,26,33,1,41,9,49,17,57,25
};

uint64_t permute(uint64_t x, int *table, int n) {
    uint64_t y = 0;
    for (int i = 0; i < n; i++) {
        y <<= 1;
        y |= (x >> (64 - table[i])) & 1;
    }
    return y;
}

uint64_t des(uint64_t data) {
    uint64_t x = permute(data, IP, 64);
    uint32_t L = x >> 32;
    uint32_t R = x & 0xFFFFFFFF;

    for (int i = 0; i < 16; i++) {
        uint32_t t = L;
        L = R;
        R = t ^ R;
    }

    x = ((uint64_t)R << 32) | L;
    return permute(x, FP, 64);
}

int main() {
    uint64_t plaintext = 0x0123456789ABCDEF;

    printf("Plaintext : %016llX\n",
           (unsigned long long)plaintext);

    uint64_t encrypted = des(plaintext);

    printf("Encrypted : %016llX\n",
           (unsigned long long)encrypted);

    uint64_t decrypted = des(encrypted);

    printf("Decrypted : %016llX\n",
           (unsigned long long)decrypted);

    return 0;
}
```


## Output:
<img width="1600" height="898" alt="image" src="https://github.com/user-attachments/assets/f890de85-0521-4f56-bd54-e39c0a6eb656" />


## Result:
  The program is executed successfully

