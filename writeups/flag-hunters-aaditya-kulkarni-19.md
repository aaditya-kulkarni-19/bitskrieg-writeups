# flag hunters-reverse engineering


## Approach
i downloaded the file and then did nano to it for inspecting the code . i could find that the 

programm was taking in user input and then printing it out

as a refrain after every stanza. there is also a code which takes i return n where n can be an 

integer from 0 to n 

and the first stanza had a suspicious naming "secret intro".

## Solution

(the actual technique, code, commands, screenshots)

it was clear that i had to some how make the first stanza print out of the programm. so i decided 

to type return 0; but it didnt work so i wrote a string followed by a return 0 

"string;return 0" and the flag was out

## Flag

picoCTF{****}

## Takeaway

read the code carefully and make sure to catch fuctions like .split() in python
