## Ex.No:2c. SIMULATING ARP/RARP PROTOCOLS

## AIM:
To write a python program for simulating ARP/RARP protocols using TCP.

## ALGORITHM:
# Client:
1. Start the program.
   
2. Using socket connection is established between client and server.
   
3. Get the IP address to be converted into MAC address.
   
4. Send this IP address to server.
   
5. Server returns the MAC address to client.
   
# Server:
1. Start the program.
   
2. Accept the socket which is created by the client.
   
3. Server maintains the table in which IP and corresponding MAC addresses are stored.
   
4. Read the IP address which is send by the client.
   
5. Map the IP address with its MAC address and return the MAC address to client. 

## PROGRAM - ARP:
# Client
~~~
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"169.254.13.114":"cc:47:40:E2:A0:9E"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except:
        c.send("Not Found".encode())
~~~

# Server
~~~
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address:")
    s.send(ip.encode())
    print("MAC address",s.recv(1024).decode())
~~~

## OUTPUT - ARP:
# Client
![image](https://github.com/K-Dharshini/2c.ARP_RARP_PROTOCOLS/assets/139334830/22c30d0d-29e2-449d-9fee-74e6c6255c54)

# Server
![image](https://github.com/K-Dharshini/2c.ARP_RARP_PROTOCOLS/assets/139334830/8838b78e-1ec0-4fa3-86ef-7c79bcea8324)

## PROGRAM - RARP:
# Client
~~~
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"}
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
~~~

# Server
~~~
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter MAC Address:")
    s.send(ip.encode())
    print("Logical address",s.recv(1024).decode())
~~~

## OUTPUT -RARP:
# Client
![image](https://github.com/K-Dharshini/2c.ARP_RARP_PROTOCOLS/assets/139334830/5cb568ca-1963-4f8e-9aff-455fbc1a7fb1)

# Server
![image](https://github.com/K-Dharshini/2c.ARP_RARP_PROTOCOLS/assets/139334830/9cea4aff-1998-4cfb-974d-e17fc442970b)

## RESULT:
Thus, the python program for simulating ARP/RARP protocols using TCP was successfully executed.
