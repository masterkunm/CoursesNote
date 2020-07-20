# Midterm Summary

* multiplexing: encapsulate data from sockets with header to become segments in the end system, then transfer to network layer.
  * Every socket has only one identifier.
  * header includes source port number field, destination port number field (UDP and TCP includes other header information).

* demultiplexing: deliver data from segments to the correct socket.

* __UDP__
  * UDP socket is full identified by dual (二元组全面标识)(include destination IP address and destination port number)(doesn't mean that the transferred segment doesn't have source info, this is UDP socket)
  * UDP data with same dest port and IP will deliver to the same socket then the same process.

  * no connection between source and destination

  * chrome QUIC protocol uses UDP on top of the reliable transfer.

  * UDP checksum -> apply 1's complement to all 16 bits word's sum, any overflow will rewind. On receiver, add checksum with all 16 bits word's sum, if we get all 1s -> correct, otherwise, corrupted happens.

* __TCP__
  * TCP socket is identified by quad (四元组标识)(include source IP, source port number, dest IP, dest port number).
  * TCP data with same dest port and IP but different source IP or port will be delivered to different sockets (except for connection request).

  * persistent HTTP: one TCP connection, use the same socket exchange message and data.
  * non-persistent HTTP: every exchange need to create a new connection and socket.

  * send/receive buffer (set up during three-way handshake)
  * MSS (Maximum segment size) (according to Maximum transmission unit (MTU))

  * __In TCP segment header field, the ACKNO is always the received sequence Number plus 1 (accumulative acknowledgement)__
  * __the sequence number is the first byte # of this TCP segment__
  * __TCP flags:__
    * ACK -> acknowledgement
    * RST, SYN, FIN -> connect/close
    * CWR, ECE -> congestion control
    * PSH -> receiver hands over data to upper layer immediately
    * URG -> urgent

  * mistakes assembly

    * __a traditional HTTP/TCP web serve, all of the sockets at the server have the same server-side port number.__

    * __the highest sequence number up to is related to ACK number.__

    * __x + 1 = 0.75x + 8 * 0.25__(remember the x increased by 1)
    ![img3](../../../img/Screen%20Shot%202020-07-13%20at%201.29.27%20pm.png)

* _reliable data transfer_
  * rdt 1.0 sender: wait for invocation -> rdt_send(data) -> packet=make_pkt(data), udt_send(packet) -> wait for invocation.....
  * rdt 1.0 receiver: wait for invocation from downside layer -> rdt_rcv(packet) -> extract(packet, data), deliver_data(data) -> wait for.....
  * rdt 2.0 bit-error rdt
    * automatic repeat request(ARQ) -> positive acknowledgment, negative acknowledgment
    * detect error (checksum)
    * (1, ACK), (0, NAK)
    * retransfer(if not rcv)

    * stop and wait (sender waits for ACK and NAK, can't do more until get reply)

    * __However, there is a fatal error, we can't sure whether the ACK and NAK is corrupted or not__, to solve this, we add a sequence number to segment. If sender/receiver accept the message as last one(same sequence number) then we know receiver/sender don't get the last message. (rdt 2.1)
  * rdt 2.2: no NAK, just (0, ACK), (1, ACK). this can also handle duplicate data packet
  * rdt 3.0: set up a timeout to wait for ACK (countdown timer), also called alternating-bit protocol
  
  * mistakes assembly
    * __packet corruption -> checksums, ACKs, sequence numbers__

    * __packet corruption and loss -> Checksums, ACKs, timeouts, sequence numbers__

    * __If packets (and ACKs and NACKs) could be lost in RDT 2.1 (or 2.2), the protocol will get stuck__

* pipelining
  * improve efficient
  * handle pipelining error
    * go-back-N
      * unidentified packet can't over N
      * if window not full, then send, otherwise wait
      * cumulative acknowledgement
      * resend from the timeout packet
    * selective repeat

  * __mistake assembly__

    * windows size <= sequence number space * 1/2
      * special condition from midterm exam(windows size 7, at least 3 bits);

* DNS
  * DNS server usually runs BIND(Berkeley internet name domain) on top of unix.
  * UDP, port 53

  * mistakes assembly
    * __A web browser needs to contact www.cse.unsw.edu.au. The minimum number of DNS requests sent is: 0.__ (local DNS cache)

* P2P

  * mistakes assembly
    * __BitTorrent uses tit-for-tat in each round to Determine to which peers to upload chunks__

* HTTP
  * non-persistent
    * each TCP transfer once

  * persistent
    * one TCP connection transfer multiple messages
    * HTTP 1.1
    * HTTP 2.0

  * HTTP request
    * request line
    * header line
      * GET
      * POST
        * entity body -> input number
      * HEAD
      * PUT
      * DELETE

  * HTTP response
    * status line
      * 200 OK
      * 301 Moved Permanently
      * 304 Not modified
      * 400 bad request
      * 404 not found
      * 505 HTTP Version not supported
    * header line
    * entity body

  * stateless protocol
    * cookie
      * in http response message header line
      * in http request message header line
      * client browser
      * Web server database

* Web cache/proxy server
  * a copy of the request object (last modified time)
  * send request with last modified time (if copy exist)

* Email
  * User agent
  * mail server
  * SMTP (simple mail transfer protocol)
  * SMTP applies to between mail server
  * user agent uses POP3(post office protocol version3), IMAP(internet mail access protocol) or HTTP to get mail from mail server