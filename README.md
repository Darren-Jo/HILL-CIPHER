# HILL CIPHER
HILL CIPHER
EX. NO: 3 AIM:
 

IMPLEMENTATION OF HILL CIPHER
 
## To write a C program to implement the hill cipher substitution techniques.

## DESCRIPTION:

Each letter is represented by a number modulo 26. Often the simple scheme A = 0, B
= 1... Z = 25, is used, but this is not an essential feature of the cipher. To encrypt a message, each block of n letters is  multiplied by an invertible n × n matrix, against modulus 26. To
decrypt the message, each block is multiplied by the inverse of the m trix used for
 
encryption. The matrix used
 
for encryption is the cipher key, and it sho
 
ld be chosen
 
randomly from the set of invertible n × n matrices (modulo 26).


## ALGORITHM:

STEP-1: Read the plain text and key from the user. STEP-2: Split the plain text into groups of length three. STEP-3: Arrange the keyword in a 3*3 matrix.
STEP-4: Multiply the two matrices to obtain the cipher text of length three.
STEP-5: Combine all these groups to get the complete cipher text.

## PROGRAM:
```
#include <stdio.h>
#include <math.h>

float encrypt[3][1], decrypt[3][1], a[3][3], b[3][3], mes[3][1], c[3][3];

void encryption();
void decryption();
void getKeyMessage();
void inverse();

int main() {
    getKeyMessage();
    encryption();
    decryption();
    return 0;
}

void encryption() {
    int i, j, k;
    for(i = 0; i < 3; i++) {
        for(j = 0; j < 1; j++) {
            encrypt[i][j] = 0;
            for(k = 0; k < 3; k++) {
                encrypt[i][j] = encrypt[i][j] + a[i][k] * mes[k][j];
            }
        }
    }

    printf("\nEncrypted string (Ciphertext) is: ");
    for(i = 0; i < 3; i++) {
        printf("%c", (char)(fmod(encrypt[i][0], 26) + 97));
    }
}

void decryption() {
    int i, j, k;
    inverse();
    
    for(i = 0; i < 3; i++) {
        for(j = 0; j < 1; j++) {
            decrypt[i][j] = 0;
            for(k = 0; k < 3; k++) {
                decrypt[i][j] = decrypt[i][j] + b[i][k] * encrypt[k][j];
            }
        }
    }

    printf("\nDecrypted string (Plaintext) is: ");
    for(i = 0; i < 3; i++) {
        printf("%c", (char)(fmod(fabs(decrypt[i][0]), 26) + 97));
    }
    printf("\n");
}

void getKeyMessage() {
    int i, j;
    char msg[4];

    printf("Enter 3x3 matrix for key (Invertible mod 26):\n");
    for(i = 0; i < 3; i++) {
        for(j = 0; j < 3; j++) {
            scanf("%f", &a[i][j]);
            c[i][j] = a[i][j];
        }
    }

    printf("\nEnter a 3-letter plaintext string (e.g., act): ");
    scanf("%s", msg);
    
    for(i = 0; i < 3; i++) {
        mes[i][0] = msg[i] - 97; // Converting characters to 0-25 range (a=0, b=1, ...)
    }
}

void inverse() {
    int i, j, k;
    float p, q;
    
    for(i = 0; i < 3; i++) {
        for(j = 0; j < 3; j++) {
            if(i == j)
                b[i][j] = 1;
            else
                b[i][j] = 0;
        }
    }
    
    for(k = 0; k < 3; k++) {
        for(i = 0; i < 3; i++) {
            p = c[i][k];
            q = c[k][k];
            for(j = 0; j < 3; j++) {
                if(i != k) {
                    c[i][j] = c[i][j] * q - p * c[k][j];
                    b[i][j] = b[i][j] * q - p * b[k][j];
                }
            }
        }
    }
    
    for(i = 0; i < 3; i++) {
        for(j = 0; j < 3; j++) {
            b[i][j] = b[i][j] / c[i][i];
        }
    }
}
```
## OUTPUT:
<img width="719" height="248" alt="image" src="https://github.com/user-attachments/assets/61ec75db-902d-41c7-a970-2eebefbd9761" />


## RESULT:
The result is verified.
