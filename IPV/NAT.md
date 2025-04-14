# How Your Router Handles Internet Requests (NAT Process)
1. Your device (e.g., phone, laptop) has a private IP (e.g., 192.168.1.10).
    - Router has two IPs:
        Public IP (assigned by ISP, e.g., 45.67.89.100) → Used to communicate with the internet.
        Private IP (e.g., 192.168.1.1) → Used inside your home network.

2. When your device wants to access a website (e.g., google.com):
It sends a request to the router. The request contains your private IP (192.168.1.10).
Router uses NAT (Network Address Translation): It replaces your private IP with its public IP (45.67.89.100).
It also creates a session (keeps track of which private IP made the request).

3. The request reaches Google’s servers:
Google sees the request coming from 45.67.89.100 (your router’s public IP).

4. Google sends back the response:
The response comes to your router’s public IP (45.67.89.100).

5. Router looks at its session table:
It checks which private IP originally made the request.
It forwards the response to the correct private IP (192.168.1.10).
Your device gets the response and loads the website! 🚀

# Router vs switchs - 
1. Router Function
Connects your home network to the internet (WAN).
Assigns private IPs to devices (via DHCP).
Performs NAT (Network Address Translation).

2. Switch Function (Inside the Router)
Handles LAN traffic between devices.
If your laptop sends data to a printer, the switch inside the router forwards it without going to the internet.

# Important IPs - 
routers IP - netstat -rn | grep default
device,s IP - ifconfig then look for en0
public_ip - curl ipinfo.io


# ✅ Final Clean Version — Laptop to Google Flow:
Your Laptop (192.168.1.10) wants to connect to google.com.

Laptop does a DNS lookup first (usually), gets Google’s public IP, say 142.250.64.78.

Now it wants to send a request to 142.250.64.78. Since that IP is outside your local network, the laptop sends the packet to its default gateway → your router’s private IP, e.g., 192.168.1.1.

This packet goes out through the laptop’s NIC (Network Interface Card):

The destination MAC address on this Ethernet frame will be the MAC address of the router.

So the laptop builds a frame:
Source MAC: Laptop’s MAC
Destination MAC: Router’s MAC
Source IP: 192.168.1.10
Destination IP: 142.250.64.78
Payload: Actual data

This frame travels to the switch:

The switch doesn’t care about IP addresses.

It simply checks the destination MAC address, looks it up in its MAC table, and forwards the frame to the router’s port.

Router receives the frame:

It checks the IP packet inside.

It sees the destination is on the internet, so it performs NAT:

It saves a record in the NAT table like:
192.168.1.10:12345 → 203.0.113.10:60001
(Your private IP and port mapped to public IP and another port)

It replaces the source IP with its public IP, e.g., 203.0.113.10.

Then it forwards the packet out to the internet via its WAN interface.

Google receives the request from IP 203.0.113.10, not from your laptop’s private IP.

Google sends back the response to 203.0.113.10.

Router receives the reply, looks up its NAT table, sees that this reply is for 192.168.1.10, and forwards it to your laptop.

The reply goes back through the switch, based on your laptop’s MAC.