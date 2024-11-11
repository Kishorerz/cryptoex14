# -Ex---14---HASH-ALGORITHM

## AIM:
To generate a simple hash of a given message using a custom hash function.
## ALGORITHM:
Input a message from the user.
Use a basic custom hash function that applies simple operations like XOR and addition on the characters of the message.
Convert the resulting hash into a hexadecimal format. Display the computed hash to the user.
Optionally verify the hash by recomputing it and comparing it with a received hash.

## PROGRAM:
```
#include <stdio.h>
#include <string.h>

// Function to compute a simple hash using XOR and addition
void computeSimpleHash(const char *message, unsigned char *hash) {
    unsigned char temp = 0;

    // Simple hash computation: XOR each character, then add its value
    for (int i = 0; message[i] != '\0'; i++) {
        temp ^= message[i];  // XOR each character
        temp += message[i];  // Add each character's value
    }

    // Store the result in the hash
    *hash = temp;
}

int main() {
    char message[256];              // Buffer for the input message
    unsigned char hash;             // Variable to store the computed hash
    char receivedHash[3];           // Buffer for input of received hash (in hex format)

    // Step 1: Input the message
    printf("Enter the message: ");
    fgets(message, sizeof(message), stdin);
    message[strcspn(message, "\n")] = '\0';  // Remove the newline character if any

    // Step 2: Compute the simple hash
    computeSimpleHash(message, &hash);

    // Step 3: Display the computed hash in hexadecimal format
    printf("Computed Hash (in hex): %02x\n", hash);

    // Optional Step 4: Verify the hash
    printf("Enter the received hash (in hex): ");
    scanf("%2s", receivedHash);  // Read exactly 2 characters for the hex value

    // Convert received hash from hex string to an unsigned char
    unsigned int receivedHashValue;
    sscanf(receivedHash, "%02x", &receivedHashValue);

    // Compare the computed hash with the received hash
    if (hash == (unsigned char)receivedHashValue) {
        printf("Hash verification successful. Message is unchanged.\n");
    } else {
        printf("Hash verification failed. Message has been altered.\n");
    }

    return 0;
}



```

## OUTPUT:
![Screenshot 2024-11-11 083205](https://github.com/user-attachments/assets/7aeb12d4-efc5-4dc1-89aa-fba78a262b10)

## RESULT:

The program for generating and verifying a simple hash of a given message using a custom hash function was executed successfully. The computed hash ensures basic integrity of the message.
