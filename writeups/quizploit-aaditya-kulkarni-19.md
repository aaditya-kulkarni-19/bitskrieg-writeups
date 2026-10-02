# quizploit - binary exploitaion


## Approach
i downloaded the binary file and source code , connected to the instance. there were questions asked based on the source code . so i inspected the code  

## Solution
connect to the instance

before that you must run the command "file vuln" . remember the info of the binary file

once you run the instance there are some basic questions about the binary file which we already 

know as we ran the command file vuln before hand

from question 4 we need to inspect the contents and code of vuln.c by running the command "cat vuln.c"

4. Question Looking at the vuln() function, what is the size of the buffer in bytes?

The buffer is declared as char buffer[0x15], which is 21 bytes in hexadecimal. This is the 

memory allocated on the stack for user input.

5. Question 0x5: How many bytes are read into the buffer?

fgets(buffer, 0x90, stdin) allows reading up to 0x90 (144) bytes. Since this exceeds the buffer size, it can overwrite memory beyond the buffer.

6. Question 0x6: Is there a buffer overflow vulnerability
Because the input length (0x90) is greater than the buffer size (0x15), a buffer overflow is

possible, potentially overwriting the stack and modifying the program’s control flow.
Question 0x7: Name a standard C function that could cause a buffer overflow.
fgets can overflow the buffer if the number of bytes read exceeds the buffer size, as it does here.

8. Question 0x8: What is the name of the function which is not called anywhere in the program?
win() exists in the source code but is never invoked by main() or any other function. This makes it a target for overflow-based exploitation.

9. Question 0x9: What type of attack could exploit this vulnerability?
Overwriting the buffer beyond its allocated size allows attackers to change the return address or other stack data, making this a classic buffer overflow attack.

10. Question 0xa: How many bytes of overflow are possible?
Maximum overflow = bytes read — buffer size = 0x90–0x15 = 0x7b. This is the number of bytes that can overwrite memory beyond the buffer.

11. Question 0xb: What protection is enabled in this binary?
NX (No-Execute) prevents executing code on the stack. Despite the overflow, injected shellcode cannot run directly; the attacker must use techniques like ROP.

12. Question 0xc: What exploitation technique could bypass NX?

Return-Oriented Programming (ROP) chains existing code snippets (gadgets) to perform desired actions without executing code on the stack, bypassing NX protections.

Using nm vuln | grep win, the function’s address is visible because the binary is not stripped. This address can be used in a crafted overflow payload to jump to win().


## Flag
picoCTF{*****}

## Takeaway
how fgets works in c and how is it different from scanf.
buffer overflow concept and we can some times use this vulnerability to hijack a control flow
