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
## Client:
```
      import socket 
      s=socket.socket() 
      s.bind(('localhost',8000)) 
      s.listen(5) 
      c,addr=s.accept() 
      address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
      print("Running")
      while True: 
                  ip=c.recv(1024).decode() 
                  try: 
                      c.send(address[ip].encode()) 
                  except KeyError: 
                      c.send("Not Found".encode())
```
## Server:
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

<img width="847" height="396" alt="442472426-4b16397e-32da-46b2-b1b3-bba9122c7324" src="https://github.com/user-attachments/assets/6d417e30-cc80-4155-976b-7d0a832cf492" />



## PROGRAM - RARP
## Client:
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
## Server:
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

<img width="837" height="408" alt="442472419-5a36847b-1292-4741-8c43-361563ba2fc5" src="https://github.com/user-attachments/assets/9f7e8522-3df1-413c-be3d-3cfbf3612a25" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
