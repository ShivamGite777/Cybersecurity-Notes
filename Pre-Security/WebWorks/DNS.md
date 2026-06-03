
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

