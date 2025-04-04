1. we type IP as decimal number like - 10.1.1.5, now computer convert this in binary number for processing.
2. Each decimal number (between dots) is called an octet, and each octet consists of 8 bits. So, 10.1.1.5 is made up of 4 octets, each represented as 8-bit binary numbers. 
3. this make ipv4 address of total of 32 bits. IPv4 addresses are 32 bits in total, which equals 4 bytes.

# BIT UNDERSTANDING - (8 bits = 1 byte)
Think of an 8-bit binary number as a row of 8 switches, each controlling a specific power of 2:
```yml
Position:  7    6    5    4    3    2    1    0
Value:    128   64   32   16    8    4    2    1
Switch:   □     □    □    □     □    □    □    □
```
1. Low-order bit (rightmost position, 0) = Worth 1 when ON
2. This is the Least Significant Bit (LSB)
   Example: 00000001 = 1 in decimal
3. High-order bit (leftmost position, 7) = Worth 128 when ON
4. This is the Most Significant Bit (MSB)
   Example: 10000000 = 128 in decimal
5. Value pattern: Each position represents 2 raised to that position's power
   Position 0 = 2⁰ = 1
   Position 1 = 2¹ = 2
   Position 2 = 2² = 4
   ...and so on until...
   Position 7 = 2⁷ = 128
6. Range: An 8-bit number can represent values from 0 to 255 (total of 256 different values).

# example - 
```yml
1. 172.16.1.59
   so lets start - 128  64  32  16  8   4   2   1  
   for 172 start sustracting from left to right and see - 
   172-128 = 44 (1 for 128).
   44 cant be substrated from 64 (0 for 64)
   44 can be with 32 = 12 (1 for 32)
   12 cant be with 16 (0 for 16)
   8 can be = 4 (1 for 8)
   4 can be with 4 (1 for 4)
   0 for 2
   0 for 1 
   final = 10101100
overall for all these 4 octate = 10101100.00010000.00000001.00111011

2. for 192.168.1.25 = 11000000.10101000.00000001.00011001
3. 231, 117 from decimal to binary = 10111011.01110101.
   11110111 bits to decimal = 1+2+4+16+32+64+128 == 247
```

# Classes in IP - we can only manage a,b,c.
Identify the IP address class, First, look at the first octet (first number) in the IP address:
Class A: 1-126 (Subnet mask: 255.0.0.0) or /8.
Class B: 128-191 (Subnet mask: 255.255.0.0) /16.
Class C: 192-223 (Subnet mask: 255.255.255.0) /24.
Class D: 224-239 (Multicast addresses).
Class E: 240-255 (Reserved addresses).

1. now if i have an IP = 192.168.1.182 (it fall in C ), so subnet mask is 255.255.255.0 and so HOSTID = 182, networkID=192.168.1.
2. overall IPs are total number -2 (1 for brodcast, 1 networkid), so if ip is 192.168.90.0 then its class C and it means - 
    192.168.90.0/24 = 256-2=254 ips available.
    - Network ID = 192.168.90.0 (first address, reserved for identifying the network).
    - Broadcast Address = 192.168.90.255 (last address, used for broadcasting messages).
    - Usable IP Range = 192.168.90.1 to 192.168.90.254.



