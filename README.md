# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.
## PROGRAM
#server
```
import socket

server = socket.socket()

server.bind(('localhost', 8000))
server.listen(1)

print("Server waiting for connection...")

conn, addr = server.accept()

print("Connected with:", addr)

while True:
    # Receive message from client
    client_msg = conn.recv(1024).decode()

    if not client_msg:
        break

    print("Client:", client_msg)

    if client_msg.lower() == "bye":
        print("Client ended the chat.")
        break

    # Send reply to client
    server_msg = input("Server: ")

    conn.send(server_msg.encode())

    if server_msg.lower() == "bye":
        print("Server ended the chat.")
        break

conn.close()
server.close()
```
#client
```
import socket

client = socket.socket()

client.connect(('localhost', 8000))

print("Connected to server.")

while True:
    # Send message to server
    msg = input("Client: ")

    client.send(msg.encode())

    if msg.lower() == "bye":
        print("Client ended the chat.")
        break

    # Receive reply from server
    reply = client.recv(1024).decode()

    print("Server:", reply)

    if reply.lower() == "bye":
        print("Server ended the chat.")
        break

client.close()
```
## OUPUT
#server
<img width="1365" height="767" alt="image" src="https://github.com/user-attachments/assets/1f7badf2-3689-4aca-9b71-83939e38d542" />
#client
<img width="1365" height="767" alt="image" src="https://github.com/user-attachments/assets/c939756c-242e-4b61-bf20-859ce860e56b" />

## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
