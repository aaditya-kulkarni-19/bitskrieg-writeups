# time stamped secrets - cryptography

## Approach
as it is mentioned that the message was encrypted using AES in ECB model , but they werent very careful with their key
to inspect the encryption.py file and found that it was a python script.There is a decrypt function that was responsible for key generation and decryption.
The program generates the key from the timestamp. It first generates a SHA256 hash of the timestamp, then slices the first 16 characters to generate the key.

## Solution
download both the files
first do cat message.txt
you will find 
<img width="1100" height="87" alt="image" src="https://github.com/user-attachments/assets/afeb0a8a-4301-4e8c-9d62-d48c1c332306" />
keep the timestamp handy as you will need it in the future procedure.

the program generates the key from the timestamp. It first generates a SHA256 hash of the timestamp, then slices the first 16 characters to generate the key.
now you need a Python script to decrypt the encrypted flag. take the help of LLM to generate the python code for you.
create a file by running the command "nano python.py" and paste the python code which looks something like  this


import hashlib
from Crypto.Cipher import AES
from Crypto.Util.Padding import unpad

# 1. Ciphertext
ciphertext_hex = "7e72f1ec54a37265e01f19b1582351f7d97304f2089d9bf489dfe8e85b8c1802"
ciphertext = bytes.fromhex(ciphertext_hex)

# 2. Search window based on the hint
hint_timestamp = 1770242619
start_time = hint_timestamp - 1000
end_time = hint_timestamp + 1000

print(f"Searching timestamps between {start_time} and {end_time}...")

# 3. Brute force loop
for guess_time in range(start_time, end_time):
    # Replicate the exact key generation from the encryption function
    key = hashlib.sha256(str(guess_time).encode()).digest()[:16]
    
    try:
        # Match the mode used in the challenge (AES-ECB)
        cipher = AES.new(key, AES.MODE_ECB)
        decrypted = cipher.decrypt(ciphertext)
        
        # Unpad the plaintext
        plaintext = unpad(decrypted, AES.block_size).decode('utf-8', errors='ignore')
        
        # Check if we successfully uncovered the flag
        if "picoCTF{" in plaintext:
            print(f"\n[+] Success! Found at timestamp: {guess_time}")
            print(f"Flag: {plaintext}")
            break
            
    except (ValueError, KeyError):
        # Mismatched keys will trigger padding errors; safely skip them
        continue
else:
    print("\n[-] Flag not found in this window. Try expanding the time range.")

run the script and get the flag


## Flag
picoCTF{*****}

## Takeaway
understanding how AES-ECB works with symmetric encryption and fixed size keys 
how timestamp was used to generate the AES key through SHA-256.
