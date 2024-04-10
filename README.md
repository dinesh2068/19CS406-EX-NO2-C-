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
## PROGRAM - ARP:
## CLIENT.PY:
```
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
## SERVER.PY:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP

## CLIENT.PY:

![image](https://github.com/dinesh2068/19CS406-EX-NO2-C-/assets/151390189/3cefa8f5-02a5-458b-a3aa-125f9a6d1b8a)

## SERVER.PY:

![Screenshot 2024-04-10 170819](https://github.com/dinesh2068/19CS406-EX-NO2-C-/assets/151390189/b713ce95-1108-4f62-8c89-92f7f4e31fb6)

## PROGRAM - RARP:
## CLIENT.PY:
```
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
```
## SERVER.PY:
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
## CLIENT.PY:

![image](https://github.com/dinesh2068/19CS406-EX-NO2-C-/assets/151390189/7932a721-35fa-4096-882c-8023a7e46399)

## SERVER.PY:

![Screenshot 2024-04-10 171045](https://github.com/dinesh2068/19CS406-EX-NO2-C-/assets/151390189/f09f0b9e-19b7-499c-8b1d-f270b20da7c1)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
