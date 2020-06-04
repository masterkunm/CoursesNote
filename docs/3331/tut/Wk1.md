# Wk1 homework questions

## probability

1. If there are N students taking COMP 3331/9331, what is the probability that none of them has a
birthday on the first day of the class? (Assume there are exactly 365 days in a year)

    ~~NoSolutionYet~~

## network question

1. What is meant by the term statistical multiplexing?

    ~~ThinkingYet~~

    ***

2. Consider two hosts, A and B, connected by a single link of rate R bps. Suppose that the two
hosts are separated by m meters, and suppose the propagation speed along the link is s meters/sec.
Host A is to send a packet of size L bits to Host B.

   * a) Express the propagation delay, dprop in terms of m and s.

    > the propagation delay is the time the transferring packet spend on the physical distance. In this question, the propagation delay is the distance between A and B divided by the propagation which is
    >
    > $$ dprop \ = \ m \ / \ s $$

    ***

   * b) Determine the transmission time of the packet, dtrans in terms of L and R.

    > the transmission time of the packet is how fast a switch/router can launch/transfer a packet to the next switch/router, which is
    > 
    > $$ dtran \ = \ L \ / \ R $$

    ***

    * c) Ignoring the processing and queuing delays, obtain an expression for the end-to-end delay.
    >
    > $$ dEndToEnd \ = \ dprop \ + \ dtran $$

    ***

    * d) Suppose Host A begins to transmit the packet at time t=0. At time t=dtrans,where is the last bit of the packet?

    > the last bit just left the Host A, heading to the destination

    ***

    * e) Suppose dprop is greater than dtrans. At time t= dtrans, where is the first bit of the packet?

    > the first bit is on the phsical way to the destination (between source end system nd destination end system)

    * (f) Suppose dprop is less than dtrans. At time t= dtrans, where is the first bit of the packet?

    > This can be a few possibles:
    >
    > * the next destination is the final end system, so the first bit of the packet arrive the end system.
    >
    > * if the processing and queuing delay are considered, the first bit may process or queue on the next switch/router.
    >
    > * it has been launched or transferred by the next switch/router.

    ***

3. It takes a single bit ten times longer to propagate over a 10Mb/s link than over a 100Mb/s link. True or False?

> False, 10Mb/s and 100Mb/s is the transmisstion rate;


4. Suppose users share a 1Mbps link. Also suppose each user requires 100 kbps when transmitting,
but each user transmits only 10 percent of the time.

   * (a) When circuit switching is used, how many users can be supported?

    > Because circuit switching requires a fixed bandwidth for stable transmission, and there is 1Mbps capable, so the result is
    >
    > $$ 1Mbps \ / \ 100kbps = 10 \ users$$

   * (b) Suppose packet switching is used for the rest of the problem. Find the probability that a given user is transmitting.

    > Analyse: 
    >
    > * one user is transmitting, a specific user
    >
    > $$ denoted \ p = 0.10 $$
    >
    > * other users are not transmitting.
    >
    > $$ (1 \ - \ p)^{N \ - \ 1}$$
    >
    > final result:
    >
    > $$ p(1 \ - \ p)^{N \ - \ 1} $$

    * (c) Suppose there are 40 users. Find the probability that at any given time, exactly n users are transmitting simultaneously(Note: You should simply express this as an expression rather than computing the exact probability value)

    > Analyse:
    >
    > * exactly n users, specific or not?
    >
    > if specific
    > $$ p^{n}(1 \ - \ p)^{N \ - \ n} $$
    >
    > if not specific, we need the help of random variable
    > $$ P(X = n) \ * \ p^{n}(1 \ - \ p)^{N \ - \ n} $$

5. Suppose there is exactly one packet switch between a sending host and the receiving host.
Assume that the transmission speed of the links between the sending host and the switch and the
switch and the receiving host are R1 and R2 respectively. Assuming that the switch uses store-andforward packet switching, what is the total end-to-end delay to send a packet of length L? Ignore
queuing, propagation and processing delays.

~~this is done~~




