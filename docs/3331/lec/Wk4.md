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

> distribute the tracker info using a distributed hash table(DHT).

