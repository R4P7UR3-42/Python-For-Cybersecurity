# Chat Application - Client Side
```Python
# This program uses sockets as well as authentication to intitiate a chat session between a client and server
import socket

# Socket
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
host = '127.0.0.1'
port = 9001

# Connect
s.connect((host, port))

# We are now connected to the server
# Client entering password
msg = s.recv(1024).decode()
if not msg:
    exit()
print(msg)
data = input('>> ')
s.sendall(str.encode(data))

# Client receiving the data
while True:
    msg = s.recv(1024).decode()
    if not msg:
        break
    print(msg)
    data = input('Enter a msg>> ')
    s.sendall(str.encode(data))
```