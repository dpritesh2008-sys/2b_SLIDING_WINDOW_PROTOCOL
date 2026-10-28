# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
To Implement sliding window protocol
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
7. 
## PROGRAM
## Client:
```
import socket

skt = socket.socket()
skt.bind(('localhost', 1234))
skt.listen(5)
c, addr = skt.accept()

size = int(input("Enter number of frames to send : "))
frames = list(range(size))
window = int(input("Enter Window Size : "))
start = 0

while start < len(frames):
    end = min(start + window, len(frames))
    c.send(str(frames[start:end]).encode())
    ack = c.recv(1024).decode()
    if ack:
        print(ack)
    start = end

c.close()
skt.close()
```
## Server:
```
import socket 
s=socket.socket() 
s.connect(('localhost',1234)) 
while True:
    data = s.recv(1024).decode()

    if not data:
        break

    print(data)

    s.send("acknowledgement received from the server".encode())
s.close()
```
## OUPUT:

<img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/317fdbd5-5bd3-4525-8ed6-a35ce217f73e" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
