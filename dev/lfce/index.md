## _ ➜  Linux Foundation Certified Engineer ➜  _

- Engineer Level certification
- Wider ranger, great depth of skills
- Focusing on `why & how things work` at a deeper level

### _ Why and how does it work this way ?? _

Find foo out!
Neat.
Wait, do I always have to answer? Well the wiki goes some way of blah and there is a story!
No no no, you're gonna `ripgrep` later for this text, ain't you?
Or more, could you just bind "Ctrl-f" to `fzf` or `rofi` and ripgrep or get just the file opened or whatever.
The story of ripgrep is that it `goes through all text` to check for that word.
So the next time I'll just ripgrep here.
Neat tools, that `actually do the job`.
This text is a pain in the ass now, just because my knowledge blahed me!

Well this looks way better `while typing` than `viewing them` as a markdown file.
Let's end this here! @@
Straightening out your thoughts I suppose.
Well I don't know now and ever! ##

Summary: `see things` - how they work and why they work eventually.

### _ The Lab Setup _

The server setup of 3 VMs : Fedora's cloned in Vmware. See network setup.

* server0 -> NAT + innet1 + innet2
* server1 -> innet1
* server2 -> innet2

`$ nmtui` is great at setting the IPs. Learn `$ nmcli` well though, had to install the tui additionally.

* server0 config --
- For the "innet1" network, server0's static IP is set to `192.168.1.1/24`.
- For the "innet2" network, server0's static IP is set to `192.168.2.1/24`.
- NAT will default DHCP and provide `internet access`. [ 192.168.163.128/24 - vmnet8]

* server1 config --
- "innet1" network with an IP of `192.168.1.100/24` & a gateway of `192.168.1.1`.
- Now `ping server0`.

* server2 config --
- "innet2" network with an IP of `192.168.2.200/24`. Let's setup `gateway later`.
- `Ping server0`.

### _ Advanced Linux Networking _

Heading this way:

Networking Topologies -> Networking Devices -> OSI Model to --
-- how data moves through a network --

  [Network Topology](ntopo.md)

### _ Advance Linux Network & Sys Administration _

I'm more interested in **how things work**.
If I know _how they work_ -- now just how to perform a task,
I become a better _problem solver_ & increase my value as a _Linux Professional_.

What's running on my system?
  [Managing Network Services](netserv.md)
  
How to monitor my system's performance?
  [Monitor System Performance]()

Manage softwares in our data centers?
  [Advanced Package Management]()
  
Manage and configure NFS (Network File System)
  [NFS]()

Get Windows and Linux systems to share resources
  [Samba]()
  
### _ Over and out! _
