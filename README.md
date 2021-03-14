#!/usr/bin/python


# This is a SMTP Enum tool to find users that can login to mail servers. 

import socket
import sys

# if Argument isnt correct then print example

if len(sys.argv) != 2:
	print "Usage: vrfy.py <username>"
	sys.exit(0)

# Create a Socket
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Connect to the remote Server  <change the IP>
connect = s.connect(('10.11.1.217',25))

# Receive the banner
banner = s.recv(1024)

print banner

# VRFY a user from the Argument 
s.send('VRFY ' + sys.argv[1] + '\r\n')
result = s.recv(1024)

print result

# Close the socket
s.close()
