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
