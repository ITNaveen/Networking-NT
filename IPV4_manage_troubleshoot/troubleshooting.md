1. if i cant connect to specific website but with others i can then there is an issue with website.

2. if i cant connect with any website then there is issue from my side then - 
   - i can try to connect to default gateway of my network (normally first ip of my network.), if this works then PC is connected with LAN fine.
   - check internet access from router, so ping recursive DNS resolver like google (8.8.8.8), if this works then router has internet access, problem seems to be DNS related.
   - check DNS resolution - nslookup google.com if ip resolve then DNS is fine, if not then there is an issue with DNS setting and so chenage DNS from google to cloudflare.

# What traceroute does:
    Shows you the number of hops:
    It lists every "hop" (i.e., network device or router) your request passes through on its way to the destination. Each hop is numbered sequentially (Hop 1, Hop 2, Hop 3, etc.).

    Helps identify where issues occur:
    If there's a problem on the network, traceroute can help pinpoint where it's happening. If one of the hops shows a timeout (* * *) or unusually high response times, it could be a sign that the issue lies at that hop or further along.

# activity monitor to access resource consumption level - 
