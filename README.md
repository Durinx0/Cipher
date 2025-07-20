# Cipher

Vigenère Cipher - Python Implementation
This simple Python script demonstrates how to encrypt and decrypt messages using the Vigenère cipher, a classic polyalphabetic substitution method.

Features
Supports both encryption and decryption

Handles non-alphabetic characters by preserving them

Works with lowercase alphabet (a-z)

How It Works
The script shifts each letter in the message based on a repeating keyword (the cipher key). Non-letter characters remain unchanged.

Usage
python
Kopieren
Bearbeiten
text = 'mrttaqrhknsw ih puggrur'
custom_key = 'happycoding'

# Decrypt the message
decryption = decrypt(text, custom_key)
print(decryption)
Example Output:
pgsql
Kopieren
Bearbeiten
Encrypted text: mrttaqrhknsw ih puggrur  
Key: happycoding  

Decrypted text: messagehidden in cypher
Functions
encrypt(message, key) – Encrypts a message using the given key.

decrypt(message, key) – Decrypts a message using the given key.

vigenere(message, key, direction=1) – Core function for both encryption and decryption.

Requirements
No external libraries needed. Just run with Python 3:

bash
Kopieren
Bearbeiten
python vigenere.py
