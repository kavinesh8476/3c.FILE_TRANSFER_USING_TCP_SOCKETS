# Ex-3c CREATION FOR FILE TRANSFER USING TCP SOCKETS
## Register Number: 212222230064
## Name: Kavinesh M
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
### Client:
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
        print('data=%s', (data))
        if not data:
            break
        f.write(data)
f.close()
print('Successfully get the file')
s.close()
print('connection closed')
```
### Server:
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
    filename='mytext.txt'
    f = open(filename,'rb')
    l = f.read(1024)
    while (l):
        conn.send(l)
        print('Sent ',repr(l))
        l = f.read(1024)
    f.close()
    print('Done sending')
    conn.send('Thank you for connecting'.encode())
    conn.close()
```
## OUTPUT
### Client:

![image](https://github.com/kavinesh8476/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/118466561/a61ba853-ab2e-431e-83f4-b92543d3f83f)



### Server:

![image](https://github.com/kavinesh8476/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/118466561/f0ea9057-cd04-4e3b-ac02-7a4cf6da2d1c)



## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
