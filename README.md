# 2c.SIMULATING ARP /RARP PROTOCOLS
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
```
SEVER.PY
import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True: 
    ip=input("Enter logical Address : ") 
    s.send(ip.encode()) 
    print("MAC Address",s.recv(1024).decode())
CLIENT.PY
import socket 
s=socket.socket() 
s.bind(('localhost',8000)) 
s.listen(5) 
c,addr=s.accept() 
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"}; 
while True: 
    ip=c.recv(1024).decode() 
    try: 
        c.send(address[ip].encode()) 
    except KeyError: 
        c.send("Not Found".encode())
```
## OUPUT - ARP
<img width="520" height="214" alt="image" src="https://github.com/user-attachments/assets/ac2760a4-c075-40a7-b47c-b03d848fd72c" />
<img width="541" height="227" alt="image" src="https://github.com/user-attachments/assets/e2b1bae4-83e2-4920-843d-c9f2cd1b7e8f" />

## PROGRAM - RARP
```
SERVER.PY
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
   ip=c.recv(1024).decode()
   try:
     c.send(address[ip].encode())
   except KeyError:
     c.send("Not Found".encode())
CLIENT.PY
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
<img width="539" height="218" alt="image" src="https://github.com/user-attachments/assets/88c25474-f692-4a3d-a82e-ef7dd0f4dbac" />
<img width="544" height="64" alt="image" src="https://github.com/user-attachments/assets/a1df9713-4066-4a17-aa03-a514df5ad5d6" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
