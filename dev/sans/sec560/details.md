## _An Attacker Needs To Know, well ..._

### _Scanning TCP Ports_

**TCP Handshake happens some way like :: **

I have got a listening service on a port.
A SYN packet arrives on that port.
The system responds with a SYN-ACK.
Then an ACK from the send to establish a connection.

If listening, a system will surely respond with a SYN-ACK ...
... regardless of the payload of the SYN packet.

Hence it gives us a reliable indication of which ports are listening.

### _TCP Behavior on Port Scanning_

Why **bother learning this** ?
It's useful to identify live systems and services.

**Case One:** A -> B || SYN + SYN-ACK
|| A learns that B is accessible on PORT 80 || 

**Case Two:** A gets a "RST-Ack" ie. a RESET.
It means, **port is CLOSED** or unaccessible on this system.

Most firewalls don't do RESETs, the hosts do. However they can.

**Case Three:**
SYN packet from A to B.
_ICMP Port Unreachable_ from B.

Meaning the port is unaccessible, likely **blocked by a firewall**.
Nmap marks this as "filtered".

**Case Four:**
SYN packet in. Nothing in response from B, likely **blocked by a firewall**.
This is **gonna slow us quite a bit**.
Nmap marks this as "filtered".

### _Results_

```bash
Since there are more closed ports than open ports, scan duration depends a lot on behavior of closed ports.

If scanning tool gets RESETs or ICMP Port Unreachables back, scans will be quick.
If nothing comes back, it has to wait for a timeout to expire before moving on to the next port.

SANS lab is setup to send RESETs to make scans faster, nice thing but no reach.
```

### _UDP Header_

Much simpler header. No need for connection, so no src/dest addresses to store.
**Source Port, Destination Port, Message Length, Checksum, Data**

There is **no initial three-way handshake** here.

We don't care for lost packets in UDP protocol.

```bash
UDP is far more simpler protocol, without tracking the state of a connection.
No connection in UDP.
Less options for scanning.
Often slower scanning.
Less reliable scanning.

Hit the right port on the right service in UDP. It's essential, so most services don't run them.
```

### _UDP Behavior While Port Scanning_

**CASES:**

* UDP in, UDP back
* UDP in, ICMP Port Unreachable back (port closed or blocked by firewall)

* UDP in, Nothing back

```bash
Ok, the port is inaccessible, but why?

Possible reasons:
a) Port is closed
b) Firewall is blocking inbound UDP probe packet
c) Firewall is blocking outbound response
d) Port is open, but it was looking for specific data in the UDP payload.

Without the payload data in the request, the target sent no response.
Nmap doesn't know the difference, so marks it "open|filtered".
```

