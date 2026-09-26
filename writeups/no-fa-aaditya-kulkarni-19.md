# NO FA - web exploitaion


## Approach
first i launched the instance of the challenge and got into the login page.

here it was asking for username and password

so i got a hint some how i need to find the user id and the password .

also the it is mentioned in the description that the data has been leaked

so i downloaded all the files available


## Solution
run the command "cat users.db"

it will mention you that the file is written in SQLite3

hence run the command "sqlite3 users.db"

you will find all the user names and their hashed login passwords

we need to get in as the admin 

so copy the hashed password of admin and open the website "Crack Station" .paste and get the password.

go to the login page and enter admin and the password "apple@123"

the page will redirect you to verify otp. 

now as we have no other way , inspect app.py which we previously downloaded and go through the code

when you carefully read the code you will find that the otp is a random no. from 0 t0 9999 and saves it in the session token and on top of that is is a flask application 

so now it is clear that the otp verification no. is saved inside you cookie

go to developers tool and copy the session cookie 

search on google "decode flask session token" and paste the session token to get the otp

when sucessfuly logged in you will find the flag

## Flag
picoCTF{***}.

## Takeaway
how to decrypt a leaked data base

how to use session cookies to find otps on flask application

using opensource decompilers


