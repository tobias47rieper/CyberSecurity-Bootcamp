## Week 12 Homework: Web Development

### Overview

In this homework, we will review the many of the concepts and tools covered in the Web Development unit. If needed, refer to the  reference sheets provided to you.

* [HTTP Reference Sheet](./HTTP_Reference.md)
* [curl Reference Sheet](./cURL_Reference.md)

#### HTTP Requests and Responses

Answer the following questions about the HTTP request and response process.

1. What type of architecture does the HTTP request and response process occur in?

        Client-Server Architecture
        Layer 7 (Application)

2. What are the different parts of an HTTP request? 

        Request Line
        Request Header
        Request Body

3. Which part of an HTTP request is optional?

        The request body

4. What are the three parts of an HTTP response?

        Status Line
        Header
        Body

5. Which number class of status codes represents errors?

        400's = Client Errors
        500's = Server Errors

6. What are the two most common request methods that a security professional will encounter?

        Get
        Post

7. Which type of HTTP request method is used for sending data?

        Post

8. Which part of an HTTP request contains the data being sent to the server?

        The Request Body

9. In which part of an HTTP response does the browser receive the web code to generate and style a web page?

        The Response Body

#### Using curl

Answer the following questions about `curl`:

10. What are the advantages of using `curl` over the browser?

        Curl is a free commandline tool that has many features including the following:
            - FTP Downloading/Uploading
            - HTTP Post
            - Proxy Support
            - SSL Connections

11. Which `curl` option is used to change the request method?

        -X

12. Which `curl` option is used to set request headers?

        -H

13. Which `curl` option is used to view the response header?

        -i

14. Which request method might an attacker use to figure out which HTTP requests an HTTP server will accept?

        Options, would be a request that an attacker would send, for it lists out all the communication options for the target.

#### Sessions and Cookies

Recall that HTTP servers need to be able to recognize clients from one another. They do this through sessions and cookies.

Answer the following questions about sessions and cookies:

15. Which response header sends a cookie to the client?

    ```HTTP
    HTTP/1.1 200 OK
    Content-type: text/html
    Set-Cookie: cart=Bob
    ```

- Set-Cookie: sends the cookie, cart=Bob

<br>

16. Which request header will continue the client's session?

    ```HTTP
    GET /cart HTTP/1.1
    Host: www.example.org
    Cookie: cart=Bob
    ```

- Cookie:

<br>

#### Example HTTP Requests and Responses

Look through the following example HTTP request and response and answer the following questions:

**HTTP Request**

```HTTP
POST /login.php HTTP/1.1
Host: example.com
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
Content-Type: application/x-www-form-urlencoded
Content-Length: 34
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Linux; Android 6.0; Nexus 5 Build/MRA58N) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.132 Mobile Safari/537.36

username=Barbara&password=password
```

17. What is the request method?

        POST

18. Which header expresses the client's preference for an encrypted response?

        Upgrade-Insecure-Requests: 1

19. Does the request have a user session associated with it?

        No

20. What kind of data is being sent from this request body?

        Login Credentials

**HTTP Response**

```HTTP
HTTP/1.1 200 OK
Date: Mon, 16 Mar 2020 17:05:43 GMT
Last-Modified: Sat, 01 Feb 2020 00:00:00 GMT
Content-Encoding: gzip
Expires: Fri, 01 May 2020 00:00:00 GMT
Server: Apache
Set-Cookie: SessionID=5
Content-Type: text/html; charset=UTF-8
Strict-Transport-Security: max-age=31536000; includeSubDomains
X-Content-Type: NoSniff
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block

[page content]
```

21. What is the response status code?

        200

22. What web server is handling this HTTP response?

        Apache

23. Does this response have a user session associated to it?

        Yes, SessionID=5

24. What kind of content is likely to be in the [page content] response body?

        Content-Type: text/html

25. If your class covered security headers, what security request headers have been included?

        HTTP Strict Transport Securty
        X-Content-Type-Options
        X-Frame-Options
        Cross Site Scripting Protection

#### Monoliths and Microservices

Answer the following questions about monoliths and microservices:

26. What are the individual components of microservices called?

        Clients
        Identity Providers
        API Gateway
        Messaging Formats
        Databases
        Static Content
        Management
        Service Discovery

27. What is a service that writes to a database and communicates to other services?

        API

28. What type of underlying technology allows for microservices to become scalable and have redundancy?

        Containers

#### Deploying and Testing a Container Set

Answer the following questions about multi-container deployment:

29. What tool can be used to deploy multiple containers at once?

        Docker Compose

30. What kind of file format is required for us to deploy a container set?

        YAML

#### Databases

31. Which type of SQL query would we use to see all of the information within a table called `customers`?

        SELECT * FROM customers;

32. Which type of SQL query would we use to enter new data into a table? (You don't need a full query, just the first part of the statement.)

        INSERT INTO customers (Name, Address, City, State, Country, ZipCode)
        VALUES ('Jason Bourne', '123 Identity St.', 'Parts Unknown', 'USA', '55555');

33. Why would we never run `DELETE FROM <table-name>;` by itself?

        Since no, WHERE, clause is specified, the whole table will be deleted.