## _ While Scanning, Run a Sniffer _

Tcpdump is designed to **capture packets** and that's it!
It's simple, light and easy to go.

Why not Wireshark? It's heavily loaded, for just the sake of _capturing some packets_.
To later _view_ those packets, Wireshark is gonna be fine.

> To sniff in Linux, I need elevated privileges.

```bash
sudo tcpdump
sudo tcpdump -D # to list interfaces
sudo tcpdump -n # numeric address/ports
sudo tcmpdump -n -i wlan0 | tee capture.dump # plain text output
```

> I'm gonna _$ sudo su -_ now.

```bash
tcpdump -n tcp and dst 10.10.10.10 # (against target)
tcpdump -n udp and src 10.10.10.10 # (from target)
tcpdump -n and port 80 and host 10.10.10.10 # (all TCP port 80 packets going to and from host)
```

### _ Useful tcpdump expressions _

Use **primitives** to formulate your expressions.

host [host]  **::** Only packets to OR from that host
net [network]  **::** Only packets for that network
port [pnum]  **::** Only packets for that port
portrange [start-end] **::** Only packets in that range of ports

src [host/port] Only packets from that host/port.
dst [host/port] Only packets to that host/port.

Also specify protocol type.
**Protocol:** ip, ether, ip6, arp, rarp, tcp, udp

Use **"and"** and **"or"** to combine these together.
Use **not** to negate.
Wrap in parentheses to group elements together.

```bash
# save the file and view packets
sudo tcpdump -w - | tee file.pcap | tcpdump -r - # binary output
```
