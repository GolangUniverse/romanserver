# Building our first service

### Design:

Our REST API should take an integer number from the client and serve back the Roman
equivalent.

The block of the API design document may look like this:

| **HTTP Verb** | **PATH**        | **Action** | **Resource** |   |
|---------------|-----------------|------------|--------------|---|
| GET           | /roman_number/2 | show       | roman_number |   |
|               |                 |            |              |   |
|               |                 |            |              |   |

### Implementation

Now, install this project with the Go command install:
    
    go install github.com/sharkzuria/romanserver

This step does two things:

Compiles the package romanNumerals and places a copy in the 
`$GOPATH/pkg` directory 

Places a binary in the `$GOPATH/bin`

We can run the preceding API server as this:

    $GOPATH/bin/romanserver

The server  should be up and running on `http://localhost:8000`
Now we can make a `GET` request to the API using a client like Browser or the `CURL` command.

Request one is as follows:
    
    curl -X GET "http://localhost:8000/roman_number/5" # Valid request

Response one as follows:

    HTTP/1.1 200 OK
    Date: Sun, 07 May 2017 11:24:32 GMT
    Content-Length: 3
    Content-Type: text/plain; charset=utf-8
    
    "V"

Let us try a few incorrectly formed requests.

Request two is as follows:(Resource out of range)

    curl -X GET "http://localhost:8000/roman_number/12" 
The response is as follows:

    HTTP/1.1 404 Not Found
    Date: Sun, 07 May 2017 11:22:38 GMT
    Content-Length: 15
    Content-Type: text/plain; charset=utf-8
    404 - Not Found

Request three is as follows:(Invalid resource)
    
    curl -X GET "http://localhost:8000/random_resource/3" 

We should get the response is as follows:

    "HTTP/1.1 400 Bad request
    Date: Sun, 07 May 2017 11:22:38 GMT
    Content-Length: 15
    Content-Type: text/plain; charset=utf-8
    400 - Bad request


[![Go Reference](https://pkg.go.dev/badge/net/http.svg)](https://pkg.go.dev/net/http)

https://github.com/PacktPublishing/Hands-On-Restful-Web-services-with-Go