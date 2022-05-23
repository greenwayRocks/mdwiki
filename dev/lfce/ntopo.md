## _ Network Topology Fundamentals && the OSI Model _

Speed at which electrons can move between devices, matters as a `design principle`.
Longer the distance, longer it takes for `data to move` between systems.

- That's the `latency` of a network ??

** Network Topology = LAN and WAN - depending on the `workload` on the network. **

### _ LAN _

* Network Adapter (RJ-45)
* Switches / Bridges [ -- _high bandwidth_ -- _low latency_ -- ]
* Switch fabric

Let's connect our high speed LAN to a remote site ( another network ) ?

### _ WAN _

This is where `routers` come. [ -- _low latency_ -- _high bandwidth_ -- ]
* Routers [ -- take traffic that's destined for another network, packages it up, 00
* 00 and ships it up to a remote location via a WAN connection.

** Switches connect computers, router connects network. **

`Applications` that **require interactivity** && \
**use a lot of data OR A database** \
can be `brought closely connected` **as though physically connected together**


PCs -> Switches -> Switch fabric -> Routers -> Firewalls

**Firewalls** control traffic that _comes_ and _goes_ out of **network**.

----


### _ Within LAN and WAN -- we have _
[1] BUS - Ethernet style, serially connected to a switch.
[2] Star - great for WANs in the 90's

* However if the **hub** went down, `everything went down`.

[3] Ring - If fails one way, _goes the other way_ round the `ring`.
[4] Full Mesh - "spider's web wala" aja ko networks.

* What is **MPLS Cloud**?

**That means - ** each of "my remote sites" has a _physical connection_ to `my WAN provider` --
**rather than to each of my other sites**.

That's great topology!

Having a **full-mess private line network** would cost a lot and would be hard to manage.

> Inside the _provider's network_, --

they provide a  **virtual full-mesh network** --
where `each of my sites` has a **direct virtual connection** to `other sites`.

**DIY** Trace the IP packet from one site to another. See if it's only _one hop away_.

> Simple implementation in my own network and decreased costs.

### _ Network of switches/routers _

In the real world, there are networks of them in the middle of a hybrid network.
For the network to be function without a loop, it would prune such links.
In layer 3, routers would choose the optimal path to go through nodes in a network.

### _ OSI (Open Systems Interconnect) Model _

A **network problem**? Starting _troubleshooting_ from here.
-- this is **the foundation** of _troubleshooting methods_ that I use when I'm working on systems (servers, workstations, networking devices).

### _ The long-lost LAYERS _

* **Physical** ➜  The actual electrical signaling on the wire.
Technologies -- NICs, hubs, modems.
Unit -- bits.

* **Data Link** ➜  encode `the bits to transfer` between _end stations_(computers, routers) - anything connected physically to L2 device.
Technologies -- NICs, hubs, modems.
Unit of transmission -- ethernet **frames**.

* **Network** ➜  IP addressing and routing. Routers help.

* **Transport**  ➜  Actual app data `chunked into segments` ready to deliver to target system. 
Think clients talking to servers. Ports are used for TCP connection.

* **Session**  ➜  Application level constructs - sth that's going on inside our client or server.
e.g. when a web server receives a request, it has its own code to start up its own concept of connection.
e.g. sockets

* **Presentation**  ➜  Encoding Application data. In web servers, using HTML, CSS.
e.g. the front-end code.

* **Application**  [➜](➜)  The thing with which _the users interact with_.
e.g. the process of an application.


----

### _ How data really moves in our networks ? _

**Key Concept ==** Encapsulation.

The OSI model utlo bata in one endstation TO sulto bata OSI model in next endstation.
Headers baddai ra hatdai janxa == packet frame == bata.

But **between networks** ?

Layers 4 through 7 aren't used for the system whose packets are destined for another network.
The info is still in the packet that is transmitted and is decoded on the destination endstation.

The key thing here is that **routers connect networks**.
