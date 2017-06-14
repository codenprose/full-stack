# full-stack
Code snippets and notes from my journey to the other side of the stack.

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
- How did you get from one server to another?
- Super helpful for debugging why a website is down.  Could be the server, could be DNS.  Trace the route.

```bash
$ traceroute danielkhunter.com
```

ICMP - Internet Control Message Packet (A way of communicating with your server via commands)

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
  - k (up)
  - j (down)
  - h (left)
  - l (right)
- insert mode
- last-line mode

## Servers
> Remote computers
- The Cloud
  - A cluster of servers
- Web Server
  - Serves HTML e.g. Nginx
- Database Server
  - AWS RDS
- Storage Server
  - AWS S3
- VPS
  - Virtual Private Servers just take a chunk of a Server make it more affordable
  - flexible
  - scalable
  - on-demand

## SSH
- Secure Socket Shell
- What's wrong with longing in with a password?  Passwords are usually easy remember and type
thus less secure.  Nobody wants to type 2399dfohaodf23kaflioq89f2g234 :)
- Public Key Authentication
  - Public Key lives on the Server
  - Private Key lives on you Computer
- Public and Private keys are very long and harder to crack
- Don't lose the private key. No one can help you :)

### Creating a SSH Key
```bash
cd ~/.ssh
ssh-keygen -t rsa
```
rsa is an ecription strategy and -t is the encription type flag


### Login to a remote Server
```bash
ssh -i ~/.ssh/<your-key> <user>@<ip-address>
-i = identity
```

### Top
- Performance monitor utility
- htop is a cleaner version but it's always best to learn the pre-installed unix/linux utils

### User Management on AWS Linux
- Add User ```adduser <username>```
- Give User root privledges ```usermod -aG sudo <username>```
- sudo = super user do, aka root
- Pro Tip: `sudo !!` will execute the last command as a super user

### Disable Root Login
- `sudo vi /etc/ssh/sshd_config`
- PermitRootLogin yes -> no
- `sudo service sshd restart`
- sshd is the daemon or "process" running ssh in the background at all times

## Nginx
- Reverse Proxy Server
  - Domain => IP Address => Nginx => Node
- `sudo yum install nginx`
- `sudo service nginx start`
- Edit config `sudo vi /etc/nginx/nginx.conf`
- `nslookup <domain>` whill show you which IP Address a domain resolves to
- `server { location / { proxy_pass http://127.0.0.1:3001/;` Send all traffic that hits `/` to an app running on port 3000

## Log Files
- `sudo mkdir -p /var/log/<logfolder>` Best practice to keep all of your log files in one place
- `sudo chown $USER /var/log/<logfolder>` Change ownership of log file to current user
- `forever start app.js >> /var/log/forever/forever.log` Write app output to log file
- `sudo tail -f /var/log/forever/forever.log` Tail a log file

## Permissions
- Change ownership of web directory to current user `sudo chown $USER:$USER /var/www` 
  - Kind of annoying to have to sudo everything in a directory where you're making a ton of changes frequently

## Security
- Check out [fail2ban](https://www.digitalocean.com/community/tutorials/how-to-protect-an-nginx-server-with-fail2ban-on-ubuntu-14-04)

## Command Line Tips & Tricks
- `rmdir tmp*` Will remove all directories that bein with `tmp`

## AWS Linux AMI & Node
- [Tutorial: Setting Up Node.js on an Amazon EC2 Instance](http://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/setting-up-node-on-ec2-instance.html)