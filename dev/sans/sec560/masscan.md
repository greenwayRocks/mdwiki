#### _ Masscan _

Nmap sends a SYN packet, waits for a SYN-ACK to complete three-way TCP handshake.
That's how systems communicate though.
However __masscan__ looks for SYN-ACKs coming back after firing at some rate, and verifies cryptographically:
"Is this from the SYN I sent?"
For the sake of speed, it can scan the entire Internet in under 6 minutes. Use scan rates wisely.

```
masscan -p22,80,443,445,1433,3389 --rate 15000 10.0.0.0/8
```

**Ports:** SSH, HTTP, HTTPS, Windows, SQL, RDP.

Let's be careful not to overwhelm any network with these tools.
If you don't use **scan rates** with Masscan (10k - 15k), this sucker will flood the gates of that network.

> What about Masscan Output ?

**Output formats:**
- list (-oL)
- xml (-oX)
- binary (-oB) == RECOMMENDED
- grepable (-oG)
- json (-oJ)

```
masscan -p0-65535 --rate 15000 --output-format binary --output-filename full.mass 10.0.0.0/8
```

To export __the binary file__ to other formats, use --read-scan.

```
masscan --read-scan full.mass --output-format xml --output-filename full.xml
```
