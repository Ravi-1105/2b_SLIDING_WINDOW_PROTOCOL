# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
### NAME: RAVIVARMAN G S
### REG.NO:212223100044
## AIM
To write a python program for Implementation of sliding Window Protocol.
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
### client
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
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
### server
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True: 
   print(s.recv(1024).decode())
   s.send("acknowledgement recived from the server".encode())
```
## OUPUT
### client
![ex-1b-client-op](https://github.com/user-attachments/assets/4a5c3fc9-414b-416f-b27a-48d000529a65)
### server
![ex-1b-server-op](https://github.com/user-attachments/assets/ffa1442e-1e24-4166-a785-fb2e162a85f0)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
