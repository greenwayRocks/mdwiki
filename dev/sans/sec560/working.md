## _How it works_

### _IPv4 Header amd TTL Field_

Lots of pieces here.
Vers=4
Hlen=5
Our packets always start with 4,5;

We also have TTL (Time To Live) ;;
TTL -> Everytime I cross a router, this is **decremented**.

In fact it should be decremented by the no. of seconds it takes to **route the packet**.
TTL is interesting, but **Come back later**.

### _IPv6 Header and Hop Limit Field_

To IPv6, there's Hop limit, and **not time limit**.
There is **enormous** space **for addresses**.

IPv6 can uniquely address every atom in the universe or something crazy - somebody said.
Basically much more to **IPv6**.

> OSI model. Most services on the Internet are **TCP** or **UDP**.

### _TCP Header and Control Bits_

We have **Source Port**, **Destination Port**.
**Sequence Number**, **Acknowledgement No.** allows _reliable connection_.

**Control bits** are also communication flags, control flags.
There are **six traditional ones**. _SYN and ACK_ are now my favorites? Well I know them.

Well TCP connection requires **TCP three way handshake** for some trust.

We'll use this capabilitly **to identify services that are listening and accessible.**

```bash
$ echo TCP handshake happens before any sort of communication.

We exchange SEQUENCE NUMBERS to establish this connection.
They are going to be INCREMENTED so that I know if i am MISSING packets.

To be able to re-transmit the lost packets and reshuffle packets in order too?
Mindblowing.

```

### _What happens!_

> A sends to B?

The sender's gonna send a packet with an ISN.
Alright, this is where I'm gonna start from `_pick one_` initial sequence number.

-- ````in my first packet from A to B, alright!```` --

We're also gonna set up **control flags** - one bit field, 1 or 0.
I'm gonna **set SYN flag** to let us know we have new data for a new connection to this target system.
ISN is a random sequence number, that should not **be predictable**.
If it is predictable, somebody might **be able to inject content** into our TCP stream.

Ack=0, TCP stack zeroes out this field.
Ack is **acknowledgement** by the receiver.

**TIP: Syn:** Seq=ISN(a) Ack=0

This is now our first packet.
Now, B has to **acknowledge our request** ;;
Assuming:
* B has no firewall in place.
* B is accessible on that port.

B is going to respond and acknowledge my packet by setting the **ACK bit** as well as **set the SYN flag to synchronize.**
We have **Two Flags Active** ^^ set to 1 ^^.
This packet is called **SYN-ACK packet**.

**i.e.** Now B has to **generate a sequence number**.
Another random value, another trouble.

**TIP: Syn-Ack:** Seq = ISN(b)  Ack = ISN(a) + 1

That +1 is for I expect this value from you next, sequencing thing.

Finally A has to **respond to B's sequence number**.
Third packet for handshake - ack:

**TIP: Ack:** Seq = ISN(a) + 1  Ack = ISN(b) + 1

In SYN-ACK packets, there are **generally no payloads**.
So no of bytes = 0.

At this point, we've exchanged initial necessary sequence numbers.
We now **have a TCP connection** for modern reliable connection.

