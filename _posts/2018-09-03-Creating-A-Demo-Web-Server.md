---
layout: post
title: Web Servers
tags: [Test, Ipsum, Markdown, Portfolio]
---

# Setting up a demo web server to interact with your client server

Today, I've experimented with setting up a web server. I wanted to understand how a HTTP transactions are made from client to a web server.

HTTP is powerful and widely supported in software, so it's a common choice for programs that need to talk to each other across the network, even if they don't look anything like a web browser.

Browsers are complicated compared to a webserver. There's no need for facny UIs because a server only needs to handle one things which are the incoming requests.

Python http.server module runs a built in web server on your personal computer.

To test python servers, you have to install python first. And determine what command to use python -m http.server 8000 or python3 -m http.server 8000 use this command to open up your web server

Running your python first web server
python -m http.server 8000

use ncat -l 9999 to open a server

It spun up an <insert an image of localhost> of http://localhost:8000

FYI for using web server to access hostnames. Use the host program to look up hostnames for example to look up google
$ host www.google.com

To loop up with the IP address us the nslookup command for example:
$ nslookup www.google.com

Basically this python server serves up files on my local disk for browser viewing.

Because this is a web server, I could access files on another computer that's on the same server. 

What's a server anyway?
A server is just a program that accepts connections from other programs on the network.

Parts of a URI
A web address is also called a URI for Uniform Resource Identifier. 

URI (Uniform Resource Identifier )are made up of several different parts
(link)
http://www.iana.org/assignments/uri-schemes/uri-schemes.xhtml

An example of a URI: https://en.wikipedia.org/wiki/Fish
his URI has three visible parts, separated by a little bit of punctuation:

https is the scheme;
en.wikipedia.org is the hostname;
and /wiki/Fish is the path.



Part 1, scheme: that tells the client hot to access the resource
Part 2, hostname: This tells the client which server to connect to.
    Why is it called a hostname? In network terminology, a host is a computer on the network; one that could host services.
Part 3, Path: identifies a particular resource on a server

The Internet tells computers apart by their IP addresses; every piece of network traffic on the Internet is labeled with the IP addresses of the sending and receiving computers. In order to connect to a web server such as www.udacity.com, a client needs to translate the hostname into an IP address. Your operating system's network configuration uses the Domain Name Service (DNS) — a set of servers maintained by Internet Service Providers (ISPs) and other network users — to look up hostnames and get back IP addresses

 What's a port number?
 IP addresses distinguish computers; port numbers distinguish programs on those computers.
 What is listening?
  "Listening" means that when the server starts up, it tells its operating system that it wants to receive connections from clients on a particular port number. 

  HTTP GET requests
You can use ncat to connect to the demo server and send it an HTTP request by hand
Sending a request
ncat 127.0.0.1 8000
GET / HTTP/1.1
Host: localhost (hit return twice)



--
  HTTP responses
  The HTTP response is made up of three parts: the status line, some headers, and a response body.

The status line is the first line of text that the server sends back. The headers are the other lines up until the first blank line. The response body is the rest — in this case, it's a piece of HTML.

Status Line: 
The status line tells the client whether the server understood the request, whether the server has the resource the client asked for, and how to proceed next. It also tells the client which dialect of HTTP the server is speaking.

Status codes:
    1xx — Informational. The request is in progress or there's another step to take.
2xx — Success! The request succeeded. The server is sending the data the client asked for.
3xx — Redirection. The server is telling the client a different URI it should redirect to. The headers will usually contain a Location header with the updated URI. Different codes tell the client whether a redirect is permanent or temporary.
4xx — Client error. The server didn't understand the client's request, or can't or won't fill it. Different codes tell the client whether it was a bad URI, a permissions problem, or another sort of error.
5xx — Server error. Something went wrong on the server side.

Header:
 Headers are a sort of metadata for the response. They aren't displayed by browsers or other clients; instead, they tell the client various information about the response.

Response Body:
Everything after that blank line is part of the response body. If the response was a success you get a copy of whatever was asked. If failed you get error messages.

