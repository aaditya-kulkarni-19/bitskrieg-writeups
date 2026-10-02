# binary digits - binary exploitation


## Approach
i downloaded the file through my terminal using the command "wget <url>" 
when i used the command "cat digits.bin" i found out that it was a raw binary file
as humans cant understand it i got to know that i need to use some application which can read binary.

## Solution
As the binary was super lenthy i chose to open cyberchef and then browse the file via import option provided in the website.
You can also copy and past the binary directly into cyberchef.
then select from binary and drag it into the recipe and select 8 in the space option
Sometimes the magical output gets activated , hence you can select that too to get direct image
once you run "from binary" , you will find a weird text . if you save the file in jpg formate, you will end up getting an image of the flag 

## Flag
picoCTF{*****}

## Takeaway
tools available on cyberchef and the download feature in the website 
recognizing the garbage text (raw bite data) format of jpg header .

