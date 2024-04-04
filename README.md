# DATA2410_Ismail_s374170_oblig2
Obligatory assignment: 2

Task 1 README

Upon implementing the web server code, troubleshooting using try-except blocks revealed an issue with locating the file path for index.html. 
The web server was unable to open the file and send its content to the web browser. 
The error message IOError: [Errno 2] No such file or directory: 'index.html' was continuously encountered. 
After exploring potential errors, I could not find any solution to the problem. 
However, the web server successfully identified the raw file path provided in the code, so index.html could be displayed in a web browser. 
When the web server is not able to find a requested file in its trajectory, the web server correctly displays a 404 Not Found message.



Task 2 README

To begin, I activate the server by running it. Then I execute the client by entering the following command in the terminal:

python3 C:\Users\liams\.vscode\s374170\webclient.py -i 192.168.56.1 -p 8000 -f r"C:\Users\liams\.vscode\s374170\index.html" 

Upon execution, the client will send an HTTP GET message to the server and display the server’s response as output. 
I received the following response from the server

HTTP/1.1 200 OK
Content-Type: text/html

The 200 OK status code indicates that the server successfully located the index.html file in the server directory, 
and the server responded accordingly with a corresponding HTML response.

Requesting a nonexistent file:

python3 C:\Users\liams\.vscode\s374170\webclient.py -i 192.168.56.1 -p 8000 -f r"C:\Users\liams\.vscode\s374170\nofile.html"
 
Server responds with:

HTTP/1.1 404 Not Found
Content-Type: text/html

The 404 Not Found status code indicates that the requested file was not found on the server, 
and the server responded accordingly with a corresponding HTML response.



Task 3 README

By utilising threading, the server creates a main thread that listens for requests at a fixed port (8000 for this server). 
Upon receiving a TCP connection request from a client, the server sets up a new TCP connection at another port (e.g. 50681) 
and services the client request in a separate thread. 
This concurrent operation allows the server to handle multiple requests simultaneously, unlike the iterative server in Task 1.

Features:
Each request/response pair is handled by a separate TCP connection socket.
Every connection socket is assigned a unique port number.
The server prints the IP address of the client and the port number for each connection.

Example of display in terminal when successfully handling a request:
Server connected by  ('192.168.56.1', 50681) 
Error: [WinError 10054] En eksisterende tilkobling ble tvangslukket av den eksterne verten

This is also the IP address the client (my computer) is running on.

Error handling:
WinError 10054: Error that occurs in HTTP connections when the client closes the connection after receiving a response from the server.

Response message:
The client displays a response message received from the server

HTTP/1.1 200 OK
Content-Type: text/html
Indicates that the requested file was successfully found and sent

HTTP/1.1 404 Not Found
Content-Type: text/html
Indicates that the requested file was not found on the server

