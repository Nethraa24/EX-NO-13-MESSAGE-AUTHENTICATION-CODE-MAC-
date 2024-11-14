# EX-NO-13-MESSAGE-AUTHENTICATION-CODE-MAC

## AIM:
To implement MESSAGE AUTHENTICATION CODE(MAC)

## ALGORITHM:

1. Message Authentication Code (MAC) is a cryptographic technique used to verify the integrity and authenticity of a message by using a secret key.

2. Initialization:
   - Choose a cryptographic hash function \( H \) (e.g., SHA-256) and a secret key \( K \).
   - The message \( M \) to be authenticated is input along with the secret key \( K \).

3. MAC Generation:
   - Compute the MAC by applying the hash function to the combination of the message \( M \) and the secret key \( K \): 
     \[
     \text{MAC}(M, K) = H(K || M)
     \]
     where \( || \) denotes concatenation of \( K \) and \( M \).

4. Verification:
   - The recipient, who knows the secret key \( K \), computes the MAC using the received message \( M \) and the same hash function.
   - The recipient compares the computed MAC with the received MAC. If they match, the message is authentic and unchanged.

5. Security: The security of the MAC relies on the secret key \( K \) and the strength of the hash function \( H \), ensuring that an attacker cannot forge a valid MAC without knowledge of the key.

## Program:
```
#include <stdio.h>
#include <string.h>
#define MAX_LEN 256 // Maximum length of the message
// FuncƟon to perform XOR encrypƟon
void encrypt(const char *input, const char *key, char *output) {
int len = strlen(input);
int key_len = strlen(key);
for (int i = 0; i < len; i++) {
output[i] = input[i] ^ key[i % key_len]; // XOR operaƟon
}
output[len] = '\0'; // Null-terminate the output string
}
// FuncƟon to perform XOR decrypƟon
void decrypt(const char *input, const char *key, char *output, int len) {
int key_len = strlen(key);
for (int i = 0; i < len; i++) {
output[i] = input[i] ^ key[i % key_len]; // XOR operaƟon
}
output[len] = '\0'; // Null-terminate the output string
}

int main() {
char message[MAX_LEN]; // Plaintext message
char key[MAX_LEN]; // Symmetric key
char input_mac[3]; // MAC input from the user
char encrypted[MAX_LEN]; // Encrypted message
char decrypted[MAX_LEN]; // Decrypted message
printf("\n Simulation of MAC Algorithm\n\n");
// Get plaintext message from the user
printf("Enter the plaintext message: ");
fgets(message, MAX_LEN, stdin);
message[strcspn(message, "\n")] = 0; // Remove newline character
// Get symmetric key from the user
printf("Enter the symmetric key: ");
fgets(key, MAX_LEN, stdin);
key[strcspn(key, "\n")] = 0; // Remove newline character
// Get MAC value from the user
printf("Enter the MAC value (in hex format): ");
scanf("%2s", input_mac); // Read the MAC input from the user
// Perform encrypƟon
encrypt(message, key, encrypted);
int encrypted_length = strlen(message);
printf("Encrypted message (raw bytes): ");
for (int i = 0; i < encrypted_length; i++) {
printf("%02x ", (unsigned char)encrypted[i]);
}
printf("\n");
decrypt(encrypted, key, decrypted, encrypted_length); 
printf("Decrypted message: %s\n", decrypted);
return 0;
}

```


## Output:
![image](https://github.com/user-attachments/assets/afcfebc0-f014-429f-96e6-2158a1fb24e8)


## Result:
The program is executed successfully.
