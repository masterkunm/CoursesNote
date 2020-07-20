# Wk4 lecture

## application layer

### Hierarchy

* H... of namespace

* H... of administered

* H... of servers

### dns

* root

* TLD (top level domain)

* authoritative NS

__once name server learns mapping, it caches mapping__.

RR format: (name, value, type, ttl);

### reliability

DNS servers are replicated(primary/secondary);

UDP used for queries (fast);

try alternate servers on timeout (exponential backoff when retrying same server)

addresses can change underneath

name could map to multiple IP address

* load-balancing
* reducing latency by picking nearby servers

multiple names for the same address

### P2P

D_p2p >= max { F/u_s, F/d_min, NF/(U_s + sum(u_i)) };

#### bitTorrent

file divided into 256KB chunks.
peers in torrent send/receive file chunks.

trackers: tracks peers participating in torrent

torrent: group of peers exchanging chunks of a file.

> always request the rarest first(balance).
>
> distribute the tracker info using a distributed hash table(DHT).

## transport layer part1

* UDP
  * connectionless transport

  * source port, dest port
  * length
  * checksum (1's complement of sum), when add numbers, carryout from the most significant bit needs to be added to the result

* TCP
  * connection-oriented reliable transport

4-tuples

1. source IP address
2. source port number 
3. dest IP address
4. dest port number

network layer finds paths through network (routing from one end host to another)

However, it doesn't guarantee

1. reliable transfer
2. guarantee paths
3. arbitrary transfer rate

### use of transport layer

provide the logical communication between end processes

### why transport layer

#### multiplexing and demultiplexing

handle data from multiple sockets, add transport header (later used for demultiplexing)

use header info to deliver received segments to correct socket

#### reliable data transfer

underlying channel perfectly reliable

* no bit errors
* no loss of packets

question: how to recover from errors

* acknowledgments (ACK)
* negative acknowledgements (NAK)

rdt 2.0/2.1/2.2/3.0
