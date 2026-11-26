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
SERVER PROGRAM:
```
import socket
port=12345
s=socket.socket()
host=socket.gethostname()
s.bind((host,port))
s.listen(5)
while True:
    conn,addr=s.accept()
    data=conn.recv(1024)
    print('Server received', repr(data))
    filename='mytext.txt'
    f=open(filename,'rb')
    l=f.read(1024)
    while (l):
        conn.send(l)
        print('Sent',repr(l))
        l=f.read(1024)
    f.close()
    print('Done sending')
    conn.send("Thank you for connecting".encode())
    conn.close()
```
CLIENT PROGRAM:
```
import socket
s=socket.socket()
host=socket.gethostname()
port=12345
s.connect((host,port))
s.send(b'Hello, server!')
with open('received_file.txt', 'wb') as f:
    while True:
        print('Receiving data...')
        data = s.recv(1024)
        print('Data=%s', (data))
        if not data:
            break
        f.write(data)
f.close()
print('Successfully received the file')
s.close()
print('Connection closed')
```
## OUPUT
<img width="975" height="985" alt="image" src="https://github.com/user-attachments/assets/b4d613c8-138f-464d-a0a2-3fa6ece086c5" />
<img width="1487" height="1032" alt="image" src="https://github.com/user-attachments/assets/ffe9f3ac-e0e1-4e79-a624-cc7aa379c2b0" />
<img width="1456" height="1017" alt="image" src="https://github.com/user-attachments/assets/04baaa02-5916-493c-a355-b957070f017d" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
