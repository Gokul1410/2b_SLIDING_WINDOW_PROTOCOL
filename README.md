# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM

### Client

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

 ### Server

 import socket
s=socket.socket()
s.connect(('localhost',8000))
while True: 
 print(s.recv(1024).decode())
 s.send("acknowledgement recived from the server".encode())
 
## OUPUT

### Client

![307230211-01fdeaa1-8fb5-483b-b789-a239fef3c9cb](https://github.com/Gokul1410/2b_SLIDING_WINDOW_PROTOCOL/assets/153058321/d7ab64ec-02a9-4a7d-a948-7eded7083ef8)

### Server

![307230226-9709b736-28c9-46de-a7a3-7a6bfa1671c9](https://github.com/Gokul1410/2b_SLIDING_WINDOW_PROTOCOL/assets/153058321/f3130a2e-18d3-490f-81e8-c550f4452cfd)


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
