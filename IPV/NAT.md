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
