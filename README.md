# 3a.CREATION FOR ECHO CLIENT AND ECHO SERVER USING TCP SOCKETS
# AIM
To write a python program for creating Echo Client and Echo Server using TCP
Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server .
4. Send and receive the message using the send function in socket.
## PROGRAM
Server.py
```

import socket

port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)

while True:
    conn, addr = s.accept()
    data = conn.recv(1024)
    print('Server received', repr(data))

    filename = 'mytext.txt'
    f = open(filename, 'rb')
    l = f.read(1024)

    while l:
        conn.send(l)
        print('Sent', repr(l))
        l = f.read(1024)

    f.close()
    print('Done sending')

    conn.send(' Thank you for connecting '.encode())
    conn.close()

```
Client.py
```

import socket

s = socket.socket()

host = socket.gethostname()
port = 60000

s.connect((host, port))

s.send("Hello server!".encode())

with open('received_file', 'wb') as f:

    while True:
        print('receiving data...')

        data = s.recv(1024)

        print('data=%s' % (data))

        if not data:
            break

        f.write(data)

print('Successfully get the file')

s.close()

print('connection closed')

```


## OUPUT


<img width="1920" height="1080" alt="Screenshot 2026-05-21 090938" src="https://github.com/user-attachments/assets/220c78e9-86a9-4ab3-8b2d-727fb2487581" />

## RESULT
Thus, the python program for creating Echo Client and Echo Server using TCP Sockets Links 
was successfully created and executed.
