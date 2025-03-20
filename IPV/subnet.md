# A big network devided into smaller network is subnet.

# subne mask - 
Binary  -       1       1       1       1       1       1       1       1   
Decimal -       128     64      32      16      8       4       2       1
Subnet_mask -   128     192     224     240     248     252     254     255

# classes - 
Class A: 1-126 (Subnet mask: 255.0.0.0) or /8.
Class B: 128-191 (Subnet mask: 255.255.0.0) /16.
Class C: 192-223 (Subnet mask: 255.255.255.0) /24.

# make subnets from ip and subnet mask - 
- example = 
1. ip = 178.68.9.0/20
Here this fall in CLASS_B, so default mask is 16 but i have 20, so 20-16= 4, so now 2 to the power 4=16 subnets i can have.
- i need to know Class and actual subnet mask then - 
subnet mask of that class - given subnet mask = x then s to the power x is subnets i can have.
- the subnet mask must be equal to or larger (higher CIDR notation) than the default mask of the IP class.

# public vs private ip - 
1. Public IP is required by hosts/device that connects directly to internet.
   private IP is not routable on the internet.
2. public IP must be globally unique.
   Private IP can be same but unique within network.
3. Public IP is routable on the internet.
   Private IP must be translated to access the internet.
4. Public IP is is assigh ISP (Internet Service Provider) or cloud providers.
   Private IP is assighn by Network administrators or automatically assigned via a router (DHCP).
