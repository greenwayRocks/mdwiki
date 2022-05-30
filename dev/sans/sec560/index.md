## _ Sec560 Stage TWO _

### _ In-depth Scanning _

> Tweak scans yourself to better find vulnerabilities. Use netcat well.

Find services and versions of those services running in **target host** system.
Use **Nessus** for automated vulnerability scanning.

### _ Scan Types _

* Network Sweeping
* Network Tracing (topology)
* Port Scanning
* OS fingerprinting
* Version Scanning
* Vulnerability Scanning

Round-robin DNS may alter a target system, while the test is occuring.
So use IP addresses to scan, and not hostnames.
**NOTE**
Also, a single IP address may be load balanced across multiple targets.
For websites thought, I may need to use a domain name.

### _ Scenarios _

> Scan 1000 hosts, all ports

All 65,536 TCP and 65,536 UDP ports.

If it took 1 second for each port, scan alone would take 4.15 years.

If it took 1 second for 100 ports, it would still take 15 days.

So what better ways?
& **Sample target machines**
& **Sample target ports**

Review **Network Firewall ruleset** and measure only reasonable ports that could make it through the firewall.

-- The firewall rules may not be updated well e.g. while pulling a system out, they don't close those ports.
-- If there's a PORT open in firewall, that service is behind it somewhere!

I can also **tweak firewall rules** to send RESETs and ICMP Port to _speed up_ scans.

### _ Hyperfast port scanning methods _

**Tools:** Masscan, ScanRand, ZMap, SuperScan, Unicornscan
**Downside:** I could create a **denial of service** (DOS) scan.

Be very careful, use a rate-limiting thing in these scanners,
I could easily take a service offline with no intention.

----

**Follow here:**
[Masscan](masscan.md)
Sniffing with [Tcpdump](tcpdump.md)
Portscanning with [Nmap](nmap.md)
