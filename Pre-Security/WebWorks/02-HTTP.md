### HTTP (HyperText Transfer Protocol)

HTTP is what's used whenever you view a website, developed by Tim Berners-Lee and his team between 1989-1991. HTTP is the set of rules used for communicating with web servers for the transmitting of webpage data, whether that is HTML, Images, Videos, etc.

### HTTPS (HyperText Transfer Protocol Secure)

HTTPS is the secure version of HTTP. HTTPS data is encrypted so it not only stops people from seeing the data you are receiving and sending, but it also gives you assurances that you're talking to the correct web server and not something impersonating it.

 
### PRACTICAL
On the mock webpage on the right there is an issue, once you've found it, click on it. What is the challenge flag?



<img width="1257" height="432" alt="image" src="https://github.com/user-attachments/assets/8b45aa01-fc87-4d82-8d18-a809194ee62f" />


### URL (Uniform Resource Locator)

A URL is the address of a resource on the Internet.

Example:
http://user:password@tryhackme.com:80/view-room?id=1#task3

## URL Components

# Scheme
 Defines the protocol.
 Examples: HTTP, HTTPS, FTP

# User
 Username and password for authentication.

# Host
 Domain name or IP address of the server.

# Port
 Specifies the port number.
 HTTP = 80
 HTTPS = 443

# Path
 Location of the resource.

Example:
/photos/cat.jpg

# Query String
 Sends extra information to the server.

Example:
?id=1
Show room 1

# Fragment
 Jumps to a specific section of a webpage.

Example:
Jump directly to Task 3 on the page

## URL = Scheme + Host + Port + Path + Query String + Fragment



### Making an HTTP Request

## Example Request

<img width="1575" height="243" alt="image" src="https://github.com/user-attachments/assets/4b21268d-dfef-4411-88b3-7ba9136f68c3" />

## Request Breakdown

# Line 1

GET / HTTP/1.1

Meaning:
 GET = Ask the server for data.
 / = Request the homepage.
 HTTP/1.1 = Use HTTP version 1.1

# Line 2
Host: tryhackme.com

Meaning:
 Tell the server which website we want to visit.
 Here, we want tryhackme.com.

# Line 3

User-Agent: Mozilla/5.0 Firefox/87.0

Meaning:
Tell the server which browser we are using.
Here, Firefox version 87.

# Line 4

Referer: https://tryhackme.com/

Meaning:
Tell the server from which webpage we came.
Here, we came from https://tryhackme.com/

# Line 5

Blank Line

Meaning:
Tells the server that the request is finished.
No more request data will be sent.

# HTTP Response

## Example Response


<img width="1540" height="592" alt="image" src="https://github.com/user-attachments/assets/b0f8c1c0-97ef-48a0-a3ca-27b7253b0b50" />

## Response Breakdown

# Line 1

HTTP/1.1 200 OK

Meaning:
 HTTP/1.1 = HTTP version used by the server.
 200 = Status code.
 OK = Request completed successfully.

Together:

The server is saying:

"Your request was successful."

# Line 2

Server: nginx/1.15.8

Meaning:
Tells us which web server software is being used.
Here, Nginx version 1.15.8.

# Line 3

Date: Fri, 11 jun 2026 10:51:03 GMT

Meaning:

 Shows the current date and time on the server.

# Line 4

Content-Type: text/html

Meaning:
Tells us what type of data is being sent.
Here, an HTML webpage.

# Line 5

Content-Length: 98

Meaning:
Size of the response data.
Here, the response contains 98 bytes.

# Line 6

Blank Line

Meaning:
Tells us the headers have finished.
The actual webpage content starts after this line.

# Lines 7-14

<html>
<head>
<title>TryHackMe</title>
</head>
<body>
Welcome To TryHackMe.com
</body>
</html>

Meaning:
This is the actual webpage content sent by the server.
The browser reads this HTML and displays the webpage.

## Key Point

HTTP Request  = Browser asks for data.
HTTP Response = Server sends data back.


### HTTP REQUEST
# GET Request

This is used for getting information from a web server.

# POST Request

This is used for submitting data to the web server and potentially creating new records

# PUT Request

This is used for submitting data to a web server to update information

# DELETE Request

This is used for deleting information/records from a web server.




### HTTP Status Codes

HTTP Status Codes tell the client (browser) the result of its request.

## Status Code Ranges

# 100-199 Information
 Request received.
 Continue sending data.

# 200-299 Success
 Request completed successfully.

# 300-399 Redirection
 Resource moved to another location.

# 400-499 Client Errors
 Problem with the client's request.

# 500-599 Server Errors
 Problem on the server side.


## Common Status Codes

# 200 OK
 Request successful.

# 201 Created
 New resource created.

# 301 Moved Permanently
 Permanent redirect.

# 302 Found
 Temporary redirect.

# 400 Bad Request
 Invalid request.

# 401 Not Authorised
 Login required.

# 403 Forbidden
 Access denied.

# 404 Not Found
 Page does not exist.

# 405 Method Not Allowed
 Wrong HTTP method used.

# 500 Internal Server Error
 Server error.

# 503 Service Unavailable
 Server overloaded or under maintenance.


 
### HTTP Headers

Headers are extra information sent between the client (browser) and server.

# Common Request Headers

## Host

 Tells the server which website we want.
 Useful when one server hosts multiple websites.
Example:
Host: tryhackme.com


## User-Agent
Tells the server which browser and version is being used.
Helps the server display the website correctly.

Example:
User-Agent: Firefox

## Content-Length
Tells the server how much data is being sent.
Helps ensure no data is missing.

Example:
Content-Length: 100
Means 100 bytes of data are being sent

## Accept-Encoding
Tells the server which compression methods the browser supports.
Makes data smaller and faster to transfer.

Example:
Accept-Encoding: gzip

## Cookie
Sends stored user information to the server.
Helps websites remember users.

Example:
Cookie: sessionID=12345

# Common Response Headers

## Set-Cookie
Sent by the server.
Stores information in the browser. 
Browser sends it back in future requests.

Example:
Set-Cookie: sessionID=12345

## Cache-Control
Tells the browser how long content should be stored in cache.
Reduces repeated download

## Content-Type

Tells the browser what type of data is being sent.

Examples:
text/html
image/png

## Content-Encoding
Tells the browser which compression method was used.
Browser decompresses the data before displaying it.

Example:
Content-Encoding: gzip

# Gzip is a compression method used to make data smaller before sending it over the Internet.




# Load Balancer
 Distributes traffic across multiple servers.
 Prevents server overload.
 Provides failover if a server goes down.

Example:

User → Load Balancer → Server 1 / Server 2

# CDN (Content Delivery Network)

 Stores static files on servers worldwide.
 Delivers files from the nearest server.
 Makes websites load faster.

Stores:
 Images
 CSS
 JavaScript
 Videos


# Database

 Stores website data.

Examples:
 MySQL
 MongoDB
 PostgreSQL

Stores
 User accounts
 Passwords
 Blog posts


# WAF (Web Application Firewall)

 Protects web applications from attacks.
 Sits between user and web server.

Functions:
 Blocks SQL Injection
 Blocks XSS
 Rate Limiting
 Detects bots

Example:

User → WAF → Web Server

### PRACTICAL
Click the "View Site" button on the right. Using everything you've learnt from the other modules, drag and drop the tiles into the correct order of how a request to a website works to reveal the flag.

<img width="505" height="857" alt="image" src="https://github.com/user-attachments/assets/fae85451-dc7e-495e-a817-6edfa0d6a154" />
<img width="308" height="791" alt="image" src="https://github.com/user-attachments/assets/eab64700-af62-4e68-a3c7-4896fbcfd0df" />
<img width="430" height="876" alt="image" src="https://github.com/user-attachments/assets/1ff6956e-8a74-4290-966d-4dac0e68dcfa" />
