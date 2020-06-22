# Wk3 lecture

## app-layer

* types

* message syntax

* message semantics

* rules

* open protocols
  * defined in RFCs
  * e.g HTTP, SMTP

* proprietary protocols
  * Skype, blue trace

### transport service app need

* data integrity
  * some apps require 100% reliable data transfer
  * other apps (audio) can tolerate some loss

* timing
  * some apps need low delay to be "effective"

* throughput
  * require amount of throughput to be "effective"
  * some other make use of whatever throughput

* security
  * encryption...

### Internet transport protocols service

* TCP service
  * reliable transport
  * flow control
  * congestion control
  * does not provide: timing, minimum throughput guarantee, security
  * connection-oriented

* UDP service
  * unreliable data transfer

### Web and HTTP

* uses TCP
  * client initiates TCP
  * server accepts TCP connection
  * HTTP messages exchanged between browser and Web server
  * TCP connection closed

* HTTP is stateless
  * no info about past client requests

* HTTP response status codes
  * 200 OK
  * 301 moved permanently
  * 400 bad request
  * 404 not found
  * 505 http version not supported
  * 451 unavailable for legal reasons
  * 429 too many requests
  * 418 I am a teapot

* request Method types HTTP/1.0: (more on HTTP/1.1)
  * GET
    * request page
  * POST
    * uploads user response to a form
  * HEAD
    * ask server to leave requested object out of response
  * below are HTTP/1.1
  * PUT
    * uploads file in entity body to path specified in URL field
  * DELETE
    * deletes file specified in the URL field
  * TRACE, OPTIONS, CONNECT, PATH
    * for persistent connections

### User-server state: cookies

1. cookie header line of http response message

2. cookie header line in next http request message

3. cookie file kept on user's host, managed by user's browser

4. back-end database at Web site

### performance of http

* page load time(PLT)

* depends on factors
  * page content/arch
  * protocols
  * network bandwidth and RRT

* improve
  * User
    * fast downloads: download speed, caching and replication
    * high availability
  * content provider
    * cost-effective (CDNS, etc...)
  * network
    * avoid overload
  * __Non-persistent__
  * __concurrent__

* persistent HTTP
  * with pipelining
  * without pipelining

* replication

### Web caching

typically cache is installed by ISP

* reduce response time

* reduce traffic 

* internet dense with caches: enables "poor" content providers to effectively deliver content

### HTTP -> HTTPS

### HTTP/2

* google SPDY

* better content structure

* improvement
  * push
  * multiplexed
  * priority
  * data compression

## Electronic mail

* three major components
  * user agents
    * mail reader
  * mail servers
    * mailbox contains incoming messages for user
    * message queue
    * SMTP protocols
  * simple mail transfer protocols: SMTP

* SMTP
  * TCP, port 25
  * direct transfer
  * three phase
    * handshaking (greeting)
    * transfer of messages
    * closure
  * command/response interaction (like HTTP, FTP)
    * commands: ASCII text
    * response: status code and phrase
  * message must be in 7-bit ASCII

* SMTP: final words
  * persistent connection
  * 7-bits ASCII
  * CRLF.CRLF determine end of message

* format
  * header line
  * body

### socket programming

### DNS

