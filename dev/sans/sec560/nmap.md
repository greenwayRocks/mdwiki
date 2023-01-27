## _Let's go Nmap-ping now!_

> Visit www.nmap.org

Not _just_ a port scanner.
Has been extended to general-purpose vulnerability scanner via NSE.
NSE stands for Nmap Scripting Engine.
`Learn its usage.`

### _Usability Features_

> --packet-trace Option

It **displays summary** of each packet Nmap sends or receives.
What's been sent back and forth? Let me know, with --packet-trace.

> Runtime Interaction?

p = Turn on packet tracing
v = Increase verbosity
d = Increase debugging level
`Hold shift` with any above key to **invert it.**
**Any other key** prints status message.

> Control scan speeds

```bash
# nmap -T [timing_option] [other options]

0: Paranoid :: 1 packet every 5 minutes
1: Sneaky :: 15 seconds between packets
2: Polite :: 0.4 seconds between packets
3: Normal :: scans in parallel
4: Aggresssive :: waits only for 1.25 seconds for **probe response**, scans in parallel
5: Insane :: waits 0.3 secs for probe response, spends only up to 15 minutes per host, parallel.

4 and 5 may not be safe and can overwhelm networks.
```

See also **Finer-Grained Nmap Timing Options** for more timing control.
**In stealth scans**, we send SYN, get SYN-ACK back and then send a RESET to reset the connection.
However **these days and ages**, stealth is not stealthy.

> Output Options

```bash
# nmap -oN [filename] target_ip
# nmap -oX [filename] target_ip
# nmap -oG [filename] target_ip
# nmap -oS [filename] target_ip
# nmap -oA [basename] target_ip
```

> Nmap and Address Probing

Nmap by default **detects if the host is up** before scanning ports.
It's two stages, perhaps.

The first stage is **Host Discovery** or **target probing**.
**Use root** for better scanning than **non-root users**, but why?
Sends ARP request if on the same subnet. **What more?**

Well, if I know the host is alive and I **want to skip Stage One**,
I can **use -Pn option**.
**Nmap will not probe a target before scanning it.**

BTW, -Pn is the same as -P0 or -PN.

> Nmap and Network Sweeping

To just probe for target hosts, ie. **see if they are alive**,

```bash
# nmap -sP [options]

# Also
# nmap -Pn [target_ip]
```

> Network Probe/Sweeping Options



