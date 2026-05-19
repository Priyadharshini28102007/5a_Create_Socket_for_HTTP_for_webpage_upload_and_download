# 5a_Create_Socket_for_HTTP_for_webpage_upload_and_download
## AIM :
To write a PYTHON program for socket for HTTP for web page upload and download
## Algorithm

1.Start the program.
<BR>
2.Get the frame size from the user
<BR>
3.To create the frame based on the user request.
<BR>
4.To send frames to server from the client side.
<BR>
5.If your frames reach the server it will send ACK signal to client otherwise it will send NACK signal to client.
<BR>
6.Stop the program
<BR>
## Program 
# server
```
import socket
import os

# Create socket
s = socket.socket()

# Bind host and port
s.bind(('localhost', 8000))

# Listen for client
s.listen(5)

print("Server waiting for connection...")

# Accept connection
c, addr = s.accept()

print("Connected to:", addr)

while True:

    # Receive hostname
    hostname = c.recv(1024).decode()

    if not hostname:
        break

    # Ping command
    response = os.popen(f"ping {hostname}").read()

    # Send result
    c.send(response.encode())

# Close socket
c.close()
s.close()
```
# client
```
client.py

import socket

# Create socket
s = socket.socket()

# Connect to server
s.connect(('localhost', 8000))

while True:

    # Input website
    ip = input("Enter the website to ping: ")

    # Send hostname
    s.send(ip.encode())

    # Receive result
    result = s.recv(4096).decode()

    print(result)
```
## OUTPUT
<img width="1112" height="344" alt="Screenshot 2026-05-19 154105" src="https://github.com/user-attachments/assets/45c6e100-a6e6-4ce7-8e4d-5c12daa4cbd6" />
<img width="1253" height="436" alt="Screenshot 2026-05-19 154124" src="https://github.com/user-attachments/assets/1f73a1ba-9b67-401a-918d-c1a2ddca7cef" />


## Result
Thus the socket for HTTP for web page upload and download created and Executed
