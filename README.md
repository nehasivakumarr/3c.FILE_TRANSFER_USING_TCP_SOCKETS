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
## Server.py
```
import socket

server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

server.bind(("127.0.0.1", 5555))

server.listen(1)

print("Server waiting for connection...")

client, addr = server.accept()

print("Connected to:", addr)

filename = input("Enter file name to send: ")

try:
    with open(filename, "rb") as file:
        data = file.read()
        client.sendall(data)

    print("File sent successfully")

except FileNotFoundError:
    print("File not found")

client.close()
server.close()
```
## Client.py
```
import socket

client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

client.connect(("127.0.0.1", 5555))

save_name = input("Enter name to save file: ")

data = client.recv(1000000)

with open(save_name, "wb") as file:
    file.write(data)

print("File received successfully")

client.close()
```
## OUTPUT
## SERVER
<img width="1547" height="897" alt="image" src="https://github.com/user-attachments/assets/7c68d55d-ebd1-4b09-b5bc-846e31cbd3d2" />

<img width="1548" height="932" alt="image" src="https://github.com/user-attachments/assets/ebb3a0ef-a623-4dfd-8c49-bf8c6ec10fb7" />
## CLIENT
<img width="1536" height="902" alt="image" src="https://github.com/user-attachments/assets/5a0a8f0d-91f2-42c1-81bf-8250ee16a035" />

<img width="1443" height="879" alt="image" src="https://github.com/user-attachments/assets/0fa2bc39-5a99-44ba-b265-9a0c2d84148d" />
## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
