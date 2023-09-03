## GOAL

1. Access any user account.

2. Use your user account to access the admin interface, perhaps by elevating your privileges or compromising the administrator account.

3. Use the admin interface to read the contents of /home/carlos/secret from the server's filesystem, and submit it using "submit solution".

## IMPORTANT

> There is always an administrator account with the username "administrator", plus a lower-privileged account usually called "carlos". 

> Each application has up to one active user, who will be logged in either as a user or an administrator. You can assume that they will visit the homepage of the site every 15 seconds, and click any links in any emails they receive from the application. You can use exploit server's "send to victim" functionality to target them with reflected vulnerabilities.

> If you find an SSRF vulnerability, you can use it to read files by accessing an internal-only service, running on localhost on port 6566.


## I. STAGE

1. XSS
2. HTTP Request Smuggling
3. Check SQLi on every f-ing input
4. Check XSS on every f-ing input

## II. STAGE

1. SQL Injection
2. HTTP Request Smuggling
3. Check SQLi on every f-ing input
4. Check XSS on every f-ing input

## III. STAGE

1. XSS
2. HTTP Request Smuggling
3. Check SQLi on every f-ing input
4. Check XSS on every f-ing input
