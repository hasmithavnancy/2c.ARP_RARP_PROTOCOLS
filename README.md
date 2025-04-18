# 2c.SIMULATING ARP /RARP PROTOCOLS
## Name:HASMITHA V NANCY
## Register No:212224040111
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
client.py
~~~
import socket 
s=socket.socket() 
s.bind(('localhost', 8000)) 
s.listen(5) 
c,addr=s.accept() 
address={"165.165.80.80":"6A:08:AA:C2:45", "165.165.79.1":"8A:BC:E3:FA:65"}; 
while True: 
    ip=c.recv(1024).decode() 
    try: 
        c.send(address[ip].encode()) 
    except KeyError: 
        c.send("Not Found".encode())
~~~
server.py
~~~
import socket 
s=socket.socket() 
s.connect(('localhost', 8000)) 
while True: 
    ip=input("Enter logical Address: ") 
    s.send(ip.encode()) 
    print("MAC Address", s.recv(1024).decode())
~~~
## OUPUT - ARP
![Screenshot 2025-04-18 110302](https://github.com/user-attachments/assets/f9fdd417-62e6-416c-8da1-b48531e85721)

## PROGRAM - RARP
client.py
~~~
import socket 
s=socket.socket() 
s.bind(('localhost', 9000)) 
s.listen(5) 
c,addr=s.accept() 
address={"6A:08:AA:C2":"192.168.1.100", "8A: BC:E3:FA": "192.168.1.99"}; 
while True: 
    ip=c.recv(1024).decode() 
    try: 
        c.send(address[ip].encode()) 
    except KeyError: 
        c.send("Not Found".encode())
~~~
server.py
~~~
import socket 
s=socket.socket() 
s.connect(('localhost', 9000)) 
while True: 
    ip=input("Enter MAC Address: ") 
    s.send(ip.encode()) 
    print("Logical Address", s.recv(1024).decode())
~~~
## OUPUT -RARP
![Screenshot 2025-04-18 110600](https://github.com/user-attachments/assets/43d098e3-7097-41f3-8b3f-5c97f752616a)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
