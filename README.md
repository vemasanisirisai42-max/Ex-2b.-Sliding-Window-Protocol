# Ex-2b.-Sliding-Window-Protocol

## AIM

To write a python program to perform sliding window protocol


## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
# Client

```


import socket

s = socket.socket()
s.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)
s.bind(('localhost', 9000))
s.listen(1)

c, addr = s.accept()

n = int(input("Enter number of frames to send : "))
w = int(input("Enter Window Size : "))

for i in range(0, n, w):
    c.send(str(list(range(i, min(i+w, n)))).encode())
    print(c.recv(1024).decode())

c.close()
s.close()


```



# server 


```

import socket

s = socket.socket()
s.connect(('localhost', 9000))

while True:
    data = s.recv(1024).decode()
    if not data:
        break

    print(data)
    s.send(b"Acknowledgement received")

s.close()


```



## OUPUT

# client 


<img width="611" height="242" alt="image" src="https://github.com/user-attachments/assets/3408bfb7-6fae-4baa-8b45-89cbb837d3f7" />







# server 

<img width="656" height="202" alt="image" src="https://github.com/user-attachments/assets/96b89457-7df8-40d9-a702-a8c48cb83403" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
