# Burp Suite Certified Practitioner Exam Study

## GOAL

1. Access any user account.

2. Use your user account to access the admin interface, perhaps by elevating your privileges or compromising the administrator account.

3. Use the admin interface to read the contents of /home/carlos/secret from the server's filesystem, and submit it using "submit solution".

## IMPORTANT

> There is always an administrator account with the username "administrator", plus a lower-privileged account usually called "carlos". 

> Each application has up to one active user, who will be logged in either as a user or an administrator. You can assume that they will visit the homepage of the site every 15 seconds, and click any links in any emails they receive from the application. You can use exploit server's "send to victim" functionality to target them with reflected vulnerabilities.

> If you find an SSRF vulnerability, you can use it to read files by accessing an internal-only service, running on localhost on port 6566.


## TOOLS

Standalone

- ysoserial
- phpgcc
- hashcat
- sqlmap


Extensions

- Param Miner
- Server-Side Prototype Pollution Scanner
- HTTP Request Smuggler


## I. STAGE

1. XSS
2. HTTP Request Smuggling
3. (?) DOM-based
4. (?) Authentication
5. (?) Web-Cache poisoning
6. HTTP Host Header

## II. STAGE

1. (?) SQL Injection
2. (?) CSRF
3. (?) Insecure Deserialization
4. (?) OAuth
5. (?) JWT
6. (?) BAC

## III. STAGE

1. (?) SSRF
2. (?) Insecure Deserialization
3. (?) XXE
4. Command Injection
5. (?) SSTI
6. Directory Traversal
7. (?) File Upload
