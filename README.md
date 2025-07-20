# Vigenère Cipher in Python

This project is a simple implementation of the **Vigenère Cipher** in Python. The script can encrypt and decrypt text messages using a custom key.

---

## Description

The Vigenère cipher is a classic method of polyalphabetic substitution. It uses a keyword to shift each letter of the plaintext by a different amount, based on the corresponding letter in the repeating key. This makes it significantly more secure than a simple Caesar cipher.

This script provides two main functions: `encrypt()` for encrypting and `decrypt()` for decrypting messages.

---

## Features

-   **Encryption & Decryption**: Converts plaintext to ciphertext and vice versa.
-   **Custom Key**: Works with any alphabetic keyword.
-   **Robust**: Preserves spaces and non-alphabetic characters in the final output.
-   **Case-Insensitive**: Treats all letters as lowercase during processing.

---

## How to Use

To use this script, you can run it directly or import its functions into your own project.

### 1. Running the Script Directly

1.  Clone or download the repository.
2.  Open the Python file (e.g., `main.py`).
3.  Modify the variables `text` and `custom_key` to suit your needs.

    -   To **encrypt** a message, call the `encrypt` function:
        ```python
        # Example for encryption
        plaintext = 'vigenere in python'
        key = 'happycoding'

        encrypted_text = encrypt(plaintext, key)
        print(f'Encrypted Text: {encrypted_text}')
        # Expected Output -> Encrypted Text: mrttaqrhknsw ih puggrur
        ```

    -   To **decrypt** a message, call the `decrypt` function:
        ```python
        # Example for decryption
        ciphertext = 'mrttaqrhknsw ih puggrur'
        key = 'happycoding'

        decrypted_text = decrypt(ciphertext, key)
        print(f'Decrypted Text: {decrypted_text}')
        # Expected Output -> Decrypted Text: vigenere in python
        ```
4.  Run the script from your terminal:
    ```bash
    python main.py
    ```

---

## Code Deep Dive

The core of the script is the `vigenere()` function, which handles both the encryption and decryption logic.

```python
def vigenere(message, key, direction=1):
    key_index = 0
    alphabet = 'abcdefghijklmnopqrstuvwxyz'
    final_message = ''

    for char in message.lower():
        # Append any non-letter character to the message
        if not char.isalpha():
            final_message += char
        else:
            # Find the right key character to encode/decode
            key_char = key[key_index % len(key)]
            key_index += 1

            # Define the offset and the encrypted/decrypted letter
            offset = alphabet.index(key_char)
            index = alphabet.find(char)
            new_index = (index + offset * direction) % len(alphabet)
            final_message += alphabet[new_index]

    return final_message

def encrypt(message, key):
    # Calls vigenere() with direction=1 for encryption
    return vigenere(message, key)

def decrypt(message, key):
    # Calls vigenere() with direction=-1 for decryption
    return vigenere(message, key, -1)
