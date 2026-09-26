# stegorsa - cryptography


## Approach
first i downloaded image and the file into my device . i opened the image manually and found 

that the and found that there was no flag printed on it .

so i got a hint that this can be solved by looking into the hidden features of the image file


## Solution
run the command "exiftool image.jpg" which is used to see metadata 

in the meta data there will be a suspicious comment which looked like written in hexadecimal format.

copy the comment form the terminal and paste it in cyberchef

choose from hexadecimal and choose 16 in the base option

copy the output as it is the private key

now go to the terminal create a fresh new file by typing nano privatekey paste the private key into it .

save the file by pressing ctrl X and then press ctrl y and press enter

now use the command prompt "openssl pkeyutl -decrypt -inkey privatekey -in flag.enc -out decrypted_file.txt"

press enter to decrypt the rsa private key and then get the flag.

## Flag
picoCTF{*****}

## Takeaway
how to decrypt a rsa private key in the command line prompt 
if the image doesn't give any hint then the hint is to look into the meta data via the exiftool
