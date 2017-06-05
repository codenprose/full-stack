# part-1

## Domains

domain - `danielkhunter.com`\
sub domain - `admin.daneilkhunter.com`

Domains simply point to ip addresses\
127.0.0.1 is always your home address

TCPIP - the system that the interet uses to communicate

### DNS
Domain Name System - "The internet phonebook"

### Ping
Is your server down? Enter the ping command.\
`ping danielkhunter.com`

### Caches
- Local cache (your computer)
- LAN DNS server (your local area network i.e. your router)
- ISP DNS server (your internet service providers cache, i.e. verizon or comcast)

If you visit google.com that ip address is more than likely cached in your browser.  However, if you visit a random russian or chinese site, dns resolution will take significantly longer.

### Security
- People are always trying to break into your computer or a virtual server.
- DDOS (distributed denial of service attacks) are the result of poor security practices.
  - Hackers take over servers that have the front door open and slame a server with a huge amount of traffic that it can't handle, thus taking it offline.

### Cache Poisoning
- https is a handshake between the client and server confirming that the requested domain is pointed to the correct ip address

### Trace Route
How did you get from one server to another?
```bash
$ traceroute danielkhunter.com
traceroute: Warning: danielkhunter.com has multiple addresses; using 52.85.90.21
traceroute to danielkhunter.com (52.85.90.21), 64 hops max, 52 byte packets
 1  fios_quantum_gateway (192.168.1.1)  2.049 ms  1.141 ms  1.008 ms
 2  l100.phlapa-vfttp-140.verizon-gni.net (108.52.121.1)  8.731 ms  8.907 ms  6.159 ms
 3  g103-0-0-14.phlapa-lcr-21.verizon-gni.net (100.41.222.40)  8.319 ms  10.729 ms  10.793 ms
 4  * * *
 5  * * *
 6  0.et-10-1-0.gw3.nyc41.alter.net (140.222.237.215)  15.116 ms  16.093 ms
    0.et-10-3-0.gw3.nyc41.alter.net (140.222.238.77)  13.866 ms
 7  amazon-gw.customer.alter.net (157.130.0.238)  16.921 ms  14.535 ms  16.639 ms
 8  52.93.1.103 (52.93.1.103)  18.569 ms
    52.93.1.105 (52.93.1.105)  22.020 ms
    52.93.1.107 (52.93.1.107)  20.802 ms
 9  52.93.1.28 (52.93.1.28)  16.126 ms
    52.93.1.58 (52.93.1.58)  17.011 ms
    52.93.1.12 (52.93.1.12)  18.587 ms
10  54.240.233.215 (54.240.233.215)  18.323 ms
    54.240.202.51 (54.240.202.51)  16.495 ms
    54.240.202.49 (54.240.202.49)  16.475 ms
11  * * *
12  * * *
13  * * *
14  server-52-85-90-21.jfk6.r.cloudfront.net (52.85.90.21)  18.563 ms  16.485 ms  16.553 ms
```

ICMP - Internet Control Message Packet (A way of communicating with your server with commands)

## VIM
> Vim isn't an editor designed to hold its users' hands.  It is a tool, the use of which must be learned."
Servers dont' have GUI's :)
- command mode
  - i (insert)
  - u (undo)
  - dd (delete line)
  - /<search term>
  - n (search from top)
  - N (search from bottom
  - Ctrl+F (page down)
  - Ctrl+B (page up))
- insert mode
- last-line mode
