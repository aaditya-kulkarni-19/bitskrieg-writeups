# old sessions - web expoitaion


## Approach
As it was written in the descrition of the ctf that  If a user logs in on a public or shared 

computer but doesn’t explicitly log out (instead simply closing the browser tab),

and session expiration dates are misconfigured, the session may remain active indefinitely.

i launched the instance and created an account. 


## Solution
As i loged in found a suspicious message about /sessions page . as i pasted it in my url i could 

see the cookie of the admin and got a hint that if i replace my current sessions cookie with 

what i found i might be able to log in as the admin

i used the developers tool on my browser , navigated to my current sessions cookie and replaced 

it with the admin cookie , reloded the page and went back to the home page . websites cant save 

users info on its own so it uses cookies to remeber the users past history

and as soon as the user opens the website it opens the page where the usser had left it .

## Flag

picoCTF{******}

## Takeaway

If i want to get in as the admin i will first try to the get the admins cookies for a week 

website. 
