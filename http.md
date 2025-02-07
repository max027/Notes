* HTTP is a protocol for fetching resources such as HTML documents. It is the foundation of any data exchange on the Web and it is a client-server protocol, which means requests are initiated by the recipient, usually the Web browser.
* Clients and servers communicate by exchanging individual messages.The messages sent by the client are called requests and the messages sent by the server as an answer are called responses.
* It is an application layer protocol that is sent over TCP, or over a TLS-encrypted TCP connection
* It is used to not only fetch hypertext documents, but also images and videos or to post content to servers, like with HTML form results.

# HTTP flow
1. Open a TCP connection
2. Send an HTTP message:
example http request
```
GET / HTTP/1.1
Host: developer.mozilla.org
Accept-Language: fr
```
3. Read the response sent by the server, such as:
```
HTTP/1.1 200 OK
Date: Sat, 09 Oct 2010 14:28:02 GMT
Server: Apache
Last-Modified: Tue, 01 Dec 2009 20:18:22 GMT
ETag: "51142bc1-7449-479b075b2891b"
Accept-Ranges: bytes
Content-Length: 29769
Content-Type: text/html

<!doctype html>… (here come the 29769 bytes of the requested web page)
```
4. Close or reuse the connection for further requests.

# A typical HTTP session
1. The client establishes a TCP connection (or the appropriate connection if the transport layer is not TCP).
2. The client sends its request, and waits for the answer.
3. The server processes the request, sending back its answer, providing a status code and appropriate data.

# Sending a client request
1. The first line contains a request method followed by its parameters:
    * the path of the document, as an absolute URL without the protocol or domain name 
    * the HTTP protocol version
    
2. Subsequent lines represent an HTTP header, giving the server information about what type of data is appropriate (for example, what language, what MIME types), or other data altering its behavior (for example, not sending an answer if it is already cached). These HTTP headers form a block which ends with an empty line.

3. The final block is an optional data block, which may contain further data mainly used by the POST method.

# Example requests
```
GET / HTTP/1.1
Host: developer.mozilla.org
Accept-Language: fr
```

# Structure of a server response
1. The first line, the status line, consists of an acknowledgment of the HTTP version used, followed by a response status code (and its brief meaning in human-readable text).
2. Subsequent lines represent specific HTTP headers, giving the client information about the data sent (for example, type, data size, compression algorithm used, hints about caching). Similarly to the block of HTTP headers for a client request, these HTTP headers form a block ending with an empty line.
3. The final block is a data block, which contains the optional data.

# Example responses
```
HTTP/1.1 200 OK
Content-Type: text/html; charset=utf-8
Content-Length: 55743
Connection: keep-alive
Cache-Control: s-maxage=300, public, max-age=0
Content-Language: en-US
Date: Thu, 06 Dec 2018 17:37:18 GMT
ETag: "2e77ad1dc6ab0b53a2996dfd4653c1c3"
Server: meinheld/0.6.1
Strict-Transport-Security: max-age=63072000
X-Content-Type-Options: nosniff
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block
Vary: Accept-Encoding,Cookie
Age: 7

<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>A simple webpage</title>
</head>
<body>
  <h1>Simple HTML webpage</h1>
  <p>Hello, world!</p>
</body>
</html>
```

## Http Post
POST is used to send data to a server to create/update a resource.
The data sent to the server with POST is stored in the request body of the HTTP request:


## Http Put 
PUT is used to send data to a server to create/update a resource.
The difference between POST and PUT is that PUT requests are idempotent.
That is, calling the same PUT request multiple times will always produce the same result.
In contrast, calling a POST request repeatedly have side effects of creating the same resource multiple times.
