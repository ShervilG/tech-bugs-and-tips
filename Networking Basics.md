TCP connection requires both a host (server) and a client with their respective IP addresses and port numbers. In the context of TCP/IP networking, each device connected to the network has an IP address, which is used for identification and routing purposes.
When establishing a TCP connection, both the client and server need to specify their IP addresses and port numbers. Here's a brief explanation of each:
1. **IP Address:**
   - **Server IP Address:** This is the IP address of the server where the service or application is running.
   - **Client IP Address:** This is the IP address of the client that is initiating the connection.
2. **Port Number:**
   - **Server Port Number:** Servers typically listen on specific port numbers for incoming connections. For example, HTTP servers often listen on port 80, and HTTPS servers on port 443. However, servers can use various port numbers depending on the service.
   - **Client Port Number:** When a client initiates a connection, it uses a randomly assigned port number, known as an ephemeral port. This port number is chosen by the client's operating system.
When a TCP connection is established, it is identified by a combination of the source and destination IP addresses and port numbers. This combination is known as a socket, and it uniquely identifies a connection.
In summary, both hosts involved in a TCP connection must have IP addresses, and each side uses a combination of IP address and port number to uniquely identify itself and the destination during the connection establishment.