# mac_os_tftp_server
Start tftp server on macos

# Folder for tftp server

	finder > go

	/private/tftpboot

# Terminal
	'''
	sudo launchctl load -F /System/Library/LaunchDaemons/tftp.plist
	sudo launchctl start com.apple.tftpd
	'''
# To verify it
	
	netstat -atp UDP | grep tftp
	
   # You should see something like this
	udp4 0 0 *.tftp *.*
	udp6 0 0 *.tftp *.*
  
# You should give permisson to the folder and all the files in that folder.

	sudo chmod 777 /private/tftpboot
	sudo chmod 777 /private/tftpboot/*

# If you want to copy to Cisco devices (Switch / AP / Router side)

	ping $IP ADDRESS OF YOUR PC

	tftp: flash:$IP ADDRESS OF YOUR PC
	source filename:$FILE NAME THAT YOU WANT TO SEND

	dir flash:

# To stop tftp server
	'''
	sudo launchctl unload -F /System/Library/LaunchDaemons/tftp.plist
	'''
