## Installation
	To get started, you need to:
		- Install an OpenSSH compatible SSH client if one is not already present.
		- Install Visual Studio Code or Visual Studio Code Insiders.
		- Install the Remote-SSH extension. If you plan to work with other remote extensions in VS Code, you may choose to install the Remote Development extension pack.

	# How to install OpenSSH for Windows
		1. Open Settings, select Apps, then select Optional Features.
		2. Scan the list to see if the OpenSSH is already installed. If not, at the top of the page, select Add a feature, then:
			- Find OpenSSH Client, then select Install
			- Find OpenSSH Server, then select Install
		3. Once setup completes, return to Apps and Optional Features and confirm OpenSSH is listed.
		4. Open the Services desktop app. (Select Start, type services.msc in the search box, and then select the Service app or press ENTER.)
		5. In the details pane, double-click OpenSSH SSH Server.
		6. On the General tab, from the Startup type drop-down menu, select Automatic.
		7. To start the service, select Start.

	# Connect to OpenSSH Server
		Once installed, you can connect to OpenSSH Server from a Windows or Windows Server device with the OpenSSH client installed.

		Run PowerShell as Administrator in CLIENT.
		From a Administrator PowerShell prompt, run the following command.

			ssh domain\username@servername
			/*
			ex: ssh DESKTOP-TCRDU4C\admin@185.250.151.210
			you can get domain and username running this command in SERVER powershell:
				[System.Security.Principal.WindowsIdentity]::GetCurrent().Name
			*/
		Once connected, you get a message similar to the following output.

			The authenticity of host 'servername (10.00.00.001)' can't be established.
			ECDSA key fingerprint is SHA256:(<a large string>).
			Are you sure you want to continue connecting (yes/no)?

		Entering yes adds that server to the list of known SSH hosts on your Windows client.

		At this point, you'll be prompted for your password. As a security precaution, your password won't be displayed as you type.
		Once connected, you'll see the Windows command shell prompt:

			domain\username@SERVERNAME C:\Users\username>

	# Uninstall OpenSSH for Windows
		To uninstall OpenSSH using Windows Settings:

		1. Open Settings, then go to Apps > Apps & Features.
		2. Go to Optional Features.
		3. In the list, select OpenSSH Client or OpenSSH Server.
		4. Select Uninstall.

		You may need to restart Windows afterwards if the service was in use at the time it was uninstalled.


## Connect to a remote host

	To connect to a remote host for the first time, follow these steps:

	1. Verify you can connect to the SSH host by running the following command from a terminal / PowerShell window replacing user@hostname as appropriate.

		ssh user@hostname or ssh user@domain@hostname
		/ ex: admin@185.250.151.210 /

	2. In VS Code, select Remote-SSH: Connect to Host... from the Command Palette (F1, Ctrl+Shift+P) and use the same user@hostname as in step 1.

	3. If VS Code cannot automatically detect the type of server you are connecting to, you will be asked to select the type manually (Linux/Windows/macOS). Once you select a platform, it will be stored in VS Code settings under the remote.SSH.remotePlatform property so you can change it at any time.

	/* When the password asked, try to enter correct password. You will get failure dialog if you enter wrong password */

	4. After a moment, VS Code will connect to the SSH server and set itself up. VS Code will keep you up-to-date using a progress notification and you can see a detailed log in the Remote - SSH output channel.

	5. After you are connected, you'll be in an empty window. You can always refer to the Status bar to see which host you are connected to.

	Clicking on the Status bar item will provide a list of remote commands while you are connected.

	6. You can then open any folder or workspace on the remote machine using File > Open... or File > Open Workspace... just as you would locally!

	From here, install any extensions you want to use when connected to the host and start editing!