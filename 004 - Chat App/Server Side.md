# Chat Application - Server Side
```Python
import socket

# Create socket and password
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
host = '127.0.0.1'
port = 9001
Password = 'password'

# Set up to take connections
s.bind((host, port))

while True:
    # Listen
    s.listen()
    # Accept connections
    client, addr = s.accept()
    pwd_challenge = 'Please enter a password'
    client.sendall(str.encode(pwd_challenge))
    pwd_attempt = client.recv(1024).decode()
    if pwd_attempt == Password:
        client.sendall(str.encode('Password is correct'))
    else:
        client.close()
        continue
        
    # We're going to send data, and if we don't receive data back, close connection
    while True:
        msg = client.recv(1024).decode()
        if not msg:
            break
        print(msg)
        if msg == 'exit':
            break
        data = input('Enter a msg>> ')
        client.sendall(str.encode(data))

    client.close()
```