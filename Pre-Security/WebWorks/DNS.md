
### DNS


DNS (Domain Name System) provides a simple way for us to communicate with devices on the internet without remembering complex numbers. Much like every house has a unique address for sending mail directly to it, every computer on the internet has its own unique address to communicate with it called an IP address. An IP address looks like the following 104.26.10.229, 4 sets of digits ranging from 0 - 255 separated by a period. When you want to visit a website, it's not exactly convenient to remember this complicated set of numbers, and that's where DNS can help. So instead of remembering 104.26.10.229, you can remember tryhackme.com 

### Domain Hierarchy
# Domain Name Structure

## TLD (Top-Level Domain)
- Rightmost part of a domain name. 
 Examples:
   .com
   .org
   .edu 
   .gov

## Types

# gTLD
- Generic Top-Level Domain
- Examples:
  .com
  .org
   .edu

# ccTLD
- Country Code Top-Level Domain
- Examples:
   .in
   .ca
   .uk

---

## Second-Level Domain (SLD)

# Taking tryhackme.com as an example, the .com part is the TLD, and tryhackme is the Second Level Domain. When registering a domain name, the second-level domain is limited to 63 characters + the TLD and can only use a-z 0-9 and hyphens (cannot start or end with hyphens or have consecutive hyphens).

- Main website name.
- Example:

tryhackme.com

SLD = tryhackme
ex = google.com
amazon.com
github.com

## Subdomain
A subdomain sits on the left-hand side of the Second-Level Domain using a period to separate it; for example, in the name admin.tryhackme.com the admin part is the subdomain. A subdomain name has the same creation restrictions as a Second-Level Domain, being limited to 63 characters and can only use a-z 0-9 and hyphens (cannot start or end with hyphens or have consecutive hyphens). You can use multiple subdomains split with periods to create longer names, such as jupiter.servers.tryhackme.com. But the length must be kept to 253 characters or less. There is no limit to the number of subdomains you can create for your domain name.

- Appears before the SLD.
- Example:

admin.tryhackme.com
Subdomain = admin

mail.google.com
blog.github.com
shop.amazon.com

 # admin = Subdomain
 # tryhackme = SLD
 # .com = TLD

 ### DNS RECORD TYPES

## A Record
Maps a domain name to an IPv4 address.

Example:
cats.com → 192.168.1.10

Memory:
A Record = IPv4

## AAAA Record
 Maps a domain name to an IPv6 address.

Example:
cats.com → 2606:4700:20::681a:be5

Memory:
AAAA Record = IPv6


## CNAME Record
These records resolve to another domain name, for example, TryHackMe's online shop has the subdomain name store.tryhackme.com which returns a CNAME record shops.shopify.com(opens in new tab). Another DNS request would then be made to shops.shopify.com(opens in new tab) to work out the IP address.
 Maps one domain name to another domain name.

Example:
# Suppose you own:
shop.cats.com

But your shop is hosted by Shopify.

# DNS Record:

shop.cats.com
      ↓
CNAME
      ↓
cats-shop.shopify.com

# Process:

shop.cats.com
      ↓
cats-shop.shopify.com
      ↓
IP Address
      ↓
Website Opens
shop.cats.com → cats-shop.shopify.com

Memory:
CNAME = Domain → Domain

## MX RECORD
 Specifies the mail server for a domain.
 Used for sending and receiving emails.

Example=
# Suppose your website is:

cats.com

Someone sends an email to:

photo@cats.com

How does the Internet know which computer stores emails for cats.com?

# It asks the MX Record.

cats.com
   ↓
MX Record
   ↓
mail.cats.com

# Meaning:

All emails for cats.com
go to mail.cats.com

cats.com → mail.cats.com

Memory:
MX = Mail Server 

## TXT RECORD
 Stores text information in DNS.
 Used for domain verification and email security.

## Email Security
 Specifies authorized email servers.
 Specifies which servers can send emails for your domain.
# Example:

cats.com
↓
TXT Record
↓
Only Google Mail can send emails for this domain

This helps prevent spam and fake emails.


## Domain Verification

 Proves ownership of a domain.

# Example:

cats.com
↓
TXT Record
↓
verification-token-12345

Google, Microsoft, etc. check this token to verify ownership.
Example:
cats.com → "verification-token"

TXT = Text Information 

### What happens when you make a DNS request


## What Happens When a DNS Record Is Not Found

## 1. LOCAL CACHE CHECK
When you request a domain name, your computer first checks its local cache to see if you've previously looked up the address recently.
If the record is not found, a request is sent to the Recursive DNS Server.

# Suppose you open:
www.cats.com

Step 1: Check Local Cache

Your computer first checks:

"Do I already know the IP address of cats.com?"

# If yes:

Use cached result 

# If no:

Ask Recursive DNS Server


## 2. RECURSIVE DNS SERVER

A Recursive DNS Server is usually provided by your ISP.
The server also checks its local cache of recently looked up domain names.
If the request cannot be found locally, a journey begins to find the correct answer.

Example:
# Computer asks Recursive DNS:

What is the IP of www.cats.com?

# Recursive DNS checks its cache.

Answer:
No 

## 3. ROOT DNS SERVER

The Recursive DNS Server queries the Root DNS Server.
The root server acts as the DNS backbone of the Internet.
Its job is to redirect the request to the correct Top Level Domain (TLD) Server.

Example:

# Recursive DNS asks Root Server:

What is the IP of www.cats.com?

# Root Server says:

I don't know the IP.
But the website ends with .com
Ask the .com TLD Server.


## 4. TLD SERVER

The TLD Server holds records for where to find the Authoritative DNS Server.
The Authoritative DNS Server is often also known as the Nameserver for the domain.

Example:
# Recursive DNS asks .com Server:

What is the IP of www.cats.com?

# TLD Server says:

I don't know the IP.
But I know the Authoritative DNS Server for cats.com.

## 5. AUTHORITATIVE DNS SERVER

The Authoritative DNS Server is responsible for storing the DNS records for the domain.
www.cats.com = 1.2.3.4 It contains the actual DNS records and returns the requested record (IP address, MX record, etc.).
# Recursive DNS asks:

What is the IP of www.cats.com?

# Authoritative Server replies:

www.cats.com = 1.2.3.4

## 6. RETURN THE RESULT

The DNS record is sent back to the Recursive DNS Server.
The Recursive DNS Server caches a local copy for future requests.
The result is then sent back to the original client (your computer).
# Computer receives:

1.2.3.4

and opens the website.
## DNS Lookup Flow

Computer
↓
Recursive DNS Server
↓
Root DNS Server
↓
TLD Server
↓
Authoritative DNS Server
↓
Recursive DNS Server
↓
Computer


## TTL (Time To Live)

DNS records contain a TTL (Time To Live) value.
TTL specifies how long a DNS record should be cached before it must be looked up again.
TTL is measured in seconds.

Example:

TTL = 3600

= Cache the DNS record for 1 hour.
