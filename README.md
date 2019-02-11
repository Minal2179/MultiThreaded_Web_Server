# MultiThreaded_Web_Server
Python multi-threaded web server

Name: Minal Shettigar
Assignment: Programming Assignment - 1
Date: 02/06/2019

BUILD A WEB SERVER

INTRODUCTION
_____________

The basic functionality of the program is to act as a web server to which client sends request and the server responds with a response along with headers that mention whether the request was served successfully or not based off of the ability of the server to handle those requests. It does so using the multithreading approach.
A high level structure of the program is as follows:
	- Forever loop:   Listen for connections
	- Accept new connection from incoming client
	- Open a thread to parse the request
	- Parse HTTP request  
		- Check if method is 'GET' or 'HEAD' else throw 501 Error
		- If request is '/' point to 'index.html'
		- For other requests:
			- check if its a valid request
				- YES:
					- check if file exists then serve them 
						- check whether you have access to file
							- YES: serve the file
							- NO: throw 403 error
					- if not download that file 
						- if file is downloadable
							- YES: download and serve the file
							- NO: throw 404 error
				- NO: throw 400 error
 	- Determine if target file exists and if permissions are set properly (return error otherwise)  
	- Transmit contents of file along with the headers to connect (by performing reads on the file and writes on the socket)  
	- Close the connection


FILES SUBMITTED
_______________

- MNHttpServer.py (Main server program that includes all the above functionality)
- Files for testing purpose: (optional file - not necessary for the program to work)
	- index.html (copy of scu.edu site)
	- media (directory containing the files to serve scu.edu site)
	- news-and-events (directory containing the files to serve scu.edu site)
	- test.txt (test txt file)
	- test.gif (test gif file)
	- test.jpg (test jpg file)
	- test.html (Custom made HTML file)
	- README.txt
	- Script.pdf
	- MSHttpServer.py (Main code)

INSTRUCTIONS TO RUN PROGRAM
___________________________

- Document root has to include index.html pointing to scu.edu site to be able to serve that request.
- Store the provided .py file in a location you have access to on the desktop.
- Run the program using following command:
	-FOR DESIGN CENTER:
	    - setup python-3.4
	    - python3
		- python MSHttpServer.py -document_root '<DOCUMENT ROOT PATH>' -PORT <PORT NUMBER - RANGE(8000 - 9999)>
	- FOR LOCAL MACHINE
		- python MSHttpServer.py -document_root '<DOCUMENT ROOT PATH>' -PORT <PORT NUMBER - RANGE(8000 - 9999)>

	example: python MSHttpServer.py -document_root '/Users/minalshettigar/Projects/' -PORT 8085
- Open the browser with localhost:<PORT_NUMBER provided>
- Headers can be seen both on terminal(command prompt) as well as Network tab on the browser after clicking on the requested resources. (List of requested resource will appear on the terminal for reference). 
