# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
```
SERVER
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)

print("Waiting for connection...")
conn, addr = s.accept()
print("Connected to", addr)

while True:
    data = conn.recv(1024).decode()
    if not data:
        break

    print("Frame received:", data)
    conn.send("ACK".encode())

conn.close()
CLIENT
import socket

s = socket.socket()
s.connect(('localhost', 8000))

n = int(input("Enter number of frames: "))

for i in range(n):
    msg = input("Enter frame: ")
    s.send(msg.encode())

    ack = s.recv(1024).decode()
    print("Received:", ack)

s.close()
```
OUTPUT
SERVER:
<img width="1920" height="1080" alt="Screenshot (57)" src="https://github.com/user-attachments/assets/d945e30a-df06-4aaf-8cce-7cfcec42d840" />
CLIENT:
<img width="1920" height="1080" alt="Screenshot (58)" src="https://github.com/user-attachments/assets/1a34f000-1b92-4d54-836a-e5fd761d0e0b" />


## OUTPUT
## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
