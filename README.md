# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM

To write a python program to perform sliding window protocol

## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
client
```
 import socket
s=socket.socket()
s.bind(('localhost',8080))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames of send:"))
l=list(range(size))
s=int(input("Enter Window size:"))
st=0
i=0
while True:
    while(i<len(l)):
        st+=s
        c.send(str(l[i:st]).encode())
        ack=c.recv(1024).decode()
        if ack:
            print(ack)
            i+=s
```

server

```
import socket
s=socket.socket()
s.connect(('localhost',8080))
while True: 
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())
```
## OUPUT

client

<img width="597" height="192" alt="Screenshot 2025-09-22 110357" src="https://github.com/user-attachments/assets/211c1fa1-836f-48b7-a958-3e8458f13f88" />

server

<img width="845" height="141" alt="Screenshot 2025-09-22 110407" src="https://github.com/user-attachments/assets/70b11cbd-88d1-42eb-a5a7-b790457e3583" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
