# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
Server
```
import socket

server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

server.bind(('localhost', 8000))
server.listen(1)

print("Server is waiting for client...")

conn, addr = server.accept()
print("Client connected:", addr)

filename = conn.recv(1024).decode()

with open("received_" + filename, "wb") as file:
    while True:
        data = conn.recv(1024)

        if not data:
            break

        file.write(data)

print("File received successfully!")

conn.close()
server.close()
```
Client
```
import socket

client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

client.connect(('localhost', 8000))

filename = input("Enter file name: ")

client.send(filename.encode())

with open(filename, "rb") as file:
    data = file.read(1024)

    while data:
        client.send(data)
        data = file.read(1024)

print("File sent successfully!")

client.close()
```
## OUPUT
<img width="1152" height="326" alt="image" src="https://github.com/user-attachments/assets/b99c6bf4-c107-408b-b551-d2878a810ae1" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
