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

### DEVELOPED BY:HARISH S
### REG NO:212223230071

## Client-ARP:
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

## Server-ARP:
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
## Client-ARP:
![WhatsApp Image 2024-10-01 at 09 10 30_6be20c1e](https://github.com/user-attachments/assets/6d67855e-6299-4a4b-a731-211597372988)

## Server-ARP:
![WhatsApp Image 2024-10-01 at 09 07 50_dd642430](https://github.com/user-attachments/assets/76875465-ab23-499c-bc3d-67c5825f19fb)



## PROGRAM - RARP

## Client -RARP:

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

## Server -RARP:

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

## Client -RARP:

![WhatsApp Image 2024-10-01 at 09 25 03_eab6fbb1](https://github.com/user-attachments/assets/3067943b-34d6-409c-8890-636e34058425)


## Server-RARP:

![WhatsApp Image 2024-10-01 at 09 21 24_242b19f1](https://github.com/user-attachments/assets/3f909d44-b160-4900-aec3-e384e60f5e7c)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
