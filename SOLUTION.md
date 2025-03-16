# HueBR Challenge 01 Solution

```
$ printf 'GET /flag.html\r\n\r\n' | nc www.example.com 80
Congratulations!
```

The solution is called Simple-Request as described on [RFC1945 > 4. HTTP Message > 4.1 Message Types](https://datatracker.ietf.org/doc/html/rfc1945#section-4.1).

```
4.  HTTP Message

4.1  Message Types

   HTTP messages consist of requests from client to server and responses
   from server to client.

       HTTP-message   = Simple-Request           ; HTTP/0.9 messages
                      | Simple-Response
                      | Full-Request             ; HTTP/1.0 messages
                      | Full-Response

   Full-Request and Full-Response use the generic message format of RFC
   822 [7] for transferring entities. Both messages may include optional
   header fields (also known as "headers") and an entity body. The
   entity body is separated from the headers by a null line (i.e., a
   line with nothing preceding the CRLF).

       Full-Request   = Request-Line             ; Section 5.1
                        *( General-Header        ; Section 4.3
                         | Request-Header        ; Section 5.2
                         | Entity-Header )       ; Section 7.1
                        CRLF
                        [ Entity-Body ]          ; Section 7.2

       Full-Response  = Status-Line              ; Section 6.1
                        *( General-Header        ; Section 4.3
                         | Response-Header       ; Section 6.2
                         | Entity-Header )       ; Section 7.1
                        CRLF
                        [ Entity-Body ]          ; Section 7.2

   Simple-Request and Simple-Response do not allow the use of any header
   information and are limited to a single request method (GET).

       Simple-Request  = "GET" SP Request-URI CRLF

       Simple-Response = [ Entity-Body ]

   Use of the Simple-Request format is discouraged because it prevents
   the server from identifying the media type of the returned entity.
```

Most of the modern web servers are still compatible with Simple-Request probably for legacy purpose.

Any filter based on the request line and using HTTP can be bypassed if the web layer is compatible with Simple-Request.
