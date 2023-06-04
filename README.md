## IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## EXP : 3
## DATE : 22-03-2023
## AIM :
To write a python program to perform sliding window protocol

## ALGORITHM :
Start the program.
Get the frame size from the user
To create the frame based on the user request.
To send frames to server from the client side.
If your frames reach the server it will send ACK signal to client otherwise it will send NACK signal to client.
Stop the program
## CLIENT PROGRAM :
```python
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send:"))
l=list(range(size))
s=int(input("Enter Window Size:"))
st=0
i=0
while True:
	while(i<len(l)):
		st+=s
		c.send(str(l[i:st]).encode())
		ack=c.recv(1024).decode()
		if ack:
			print(ack)
			i+=s
```

## SERVER PROGRAM :
```python
import socket![Uploading server2.png…]()

s=socket.socket()
s.connect(('localhost',8000))
while True:
	print(s.recv(1024).decode())
	s.send("acknowledgement recieved from the server".encode())
```

## CLIENT OUTPUT :

![ex 3 cl output](https://github.com/MrSanthosh-dev/EX-3/assets/117916573/94ac36cc-6d03-4793-b47d-4fa18ca953b0)

## SERVER OUTPUT :
![ex 3 se output](https://github.com/MrSanthosh-dev/EX-3/assets/117916573/368d010b-f849-4747-8ec2-53fbca8358c0)


## RESULT :
Thus, python program to perform stop and wait protocol was successfully executed
