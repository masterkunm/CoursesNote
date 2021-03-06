# WK1 Lec

## What is internet

### Structure view

internet is the combination of 3 parts:

* connected device (including hosts/endSystems which run net app)

* communication link (including fiber, copper, radio, satellite, transmission unit call bandwidth)

* packet switch (forward chunks of data, such as switch and router)

### Service view

* network of networks

* protocol (sending message and receiving message)

* internet standard (RFC, IETF: internet engineering task force)

## What is a protocol

It is more like a standard method to tell you how to send message and receive message

protocols define format, order of msgs sent and received among network entities, and actions taken on msgs transmission, receipt.

## Edge network

Client and server, which are end systems/hosts, they all are edge network

### How do they connect together

use the personal access network (residential net, institution access network, mobile access network) to connect with the edge router.

### Type

* digital subscriber line (ADSL: asymmetric digital subscriber line)
  * DSL modem <-> splitter <-> DSLAM(DSL access multiplexer)
  * direct access to central office

* cable network
  * FDM (frequency division multiplexing), different channels are transmitted in different frequency bands.
  * HFC: hybrid fiber coax
  * network of cable, fiber attach home to ISP router (through headend: cable modem termination system)

* fiber to the home/premise/curb
  * can be from headend or central office
  * also need DSL modem

* Ethernet

* wireless access network
  * wireless lan
  * wide area wireless

### Physical media

* twisted pair

* fiber optical path

* coax

* radio

## Network Core

* interconnected routers/switches
  * circuit switching
    * TDM / FDM
  * packet switching

## delay, loss, throughput in networks

### why delay and loss happened

packets are transmitting (delay).

packets are queuing (delay).

arriving packets drop if no free buffer (store and transmit) / arrival rate to link (temporarily) exceeds output link capacity.

### throughput

rate (bits/time unit) at which bits transferred between sender/receiver.

## protocol layer, service model

Three design step:

* break down the problem into tasks

* organize these task

* decide who does what

~~next~~

1. prepare data. (application layer)

2. ensure the packet reach the dest process. (transport layer)

3. deliver packets through global network. (network layer)

4. deliver packets to next hop within local network. (datalink layer)

5. put bits/packets on weir or trans, medium. (physical layer)