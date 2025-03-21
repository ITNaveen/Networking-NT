lets say computer A wants to send message to B, so overall message of A will be devided on chunks, for example -  message from A devided in 5 chunks.
Now first chunk number 5 will go to B and B will acknowledge and then piece 4 and so on.
If any of the chunk delivery wouldn,t get acknowledge back then A can retry this again to B until B provde acknowledgement.
This way with TCP, we are sure message is always recived.

# TCP windowing - 
How Acknowledgment Works in TCP Windowing:
A sends a batch of chunks (based on B’s window size).
B receives them and sends an acknowledgment (ACK).
The ACK tells A which data has been received and how much more B can accept.
A uses this information to adjust the next batch of chunks.
Ex - 
🔹 B’s initial window size = 5
🔹 A has 10 chunks to send

Step-by-Step Transmission & ACKs:
1️⃣ A sends chunks [1, 2, 3, 4, 5] (because B’s window size is 5)
2️⃣ B receives these 5 chunks and sends ACK:

ACK 6 (meaning "I have received up to chunk 5, send more")
B also updates the window size (e.g., 5 more chunks allowed)
3️⃣ A sends chunks [6, 7, 8, 9, 10]
4️⃣ B receives them and sends ACK 11 (meaning "I have received everything up to chunk 10").

