# TCP Traffic Generator
A simple Python script with no dependencies for generating quick TCP traffic to test a port on an endpoint. 

# Prerequisites
- Install [Python](https://www.python.org/).
- Ensure Python is in your `PATH`. In Windows, this option may need to be selected during the installation process.
- In Windows, ensure that `.py` files are associated with Python. This option may need to be selected during the installation process.


# Installation
If you don't want to type out `python tcpgen.py` or `python3 tcpgen.py` every time you want to run the script, you can follow these instructions.
## Windows
- Create the `%USERPROFILE%\.local\` and `%USERPROFILE%\.local\bin\` directories
- Add `%USERPROFILE%\.local\bin` to your `PATH` and `.PY` to your `PATHTEXT`
  - Open `File Explorer` > Right click `This PC` > Click `Properties` > Click `Advanced System Settings` > Click `Environment Variables`
  - Select `Path` for your user (not your system), click `Edit`, and add `%USERPROFILE%\.local\bin`
  - Select `PATHTEXT` for your system, click `Edit`, and add `.PY` to the end of the list
- Move the `tcpgen.py` file to the `%USERPROFILE%\.local\bin\` directory
- Open a new CMD instance and run `tcpgen`

## Linux/MacOS
- Ensure that `$HOME/.local/bin` is added to your `PATH`. Instructions may vary. If using Bash:
  - Search `~/.bashrc` with the command `cat ~/.bashrc | grep PATH` 
  - If `export PATH=$HOME/.local/bin:$PATH` isn't part of the output, add it to `~/.bashrc`
- Some distros use the `python` command, and others use `python3`. If `/usr/bin/env python` returns an error, change the shebang to `#!/usr/bin/env python3`
- Move the `tcpgen.py` file to `~/.local/bin/` with the name `tcpgen` (extension not necessary)
- `chmod u+x ~/.local/bin/tcpgen` to make the file executable.
- Open a new terminal session and run `tcpgen`

# Usage
## No CLI Args
You can use the script without any arguments passed. For example, if using Windows, you might do this:
```
>tcpgen
Hostname/IP: localhost
Resolved localhost to 127.0.0.1
Ports (separated by space, e.g. 22 80 443): 22 80 443 3389
[output omitted]
Hostname/IP:
Exiting...

>
```
This will prompt you for a host and a list of ports until Ctrl-C is detected.
## One CLI Arg
If there is only one argument, the script expects a hostname or IP address. For example:
```
>tcpgen localhost
Resolved localhost to 127.0.0.1
[output omitted]

>
```

By default, port 22 will be used. You can change this by setting the `DEFAULT_PORTS` variable. For example:
```
DEFAULT_PORTS = [22, 80, 443]
```

## More Than One CLI Arg
If there are multiple arguments, the first must be the hostname or IP address. The rest are expected to be ports. For example:
```
>tcpgen localhost 22 80 443 3389
Resolved localhost to 127.0.0.1
[output omitted]

>
```

# Example
Here's what it looks like:

![Windows](./.github/windows_example.png)

![Ubuntu](./.github/ubuntu_example.png)

Note that the error messages in Windows are different than Linux. In Windows, if the traffic reaches the destination but the traffic is rejected, the traffic will appear to be timed out or dropped (even with Defender Firewall turned off). Ubuntu, however, more accurately displays the error message "Connection refused". This is not a bug, but rather a difference in how the operating systems display rejected traffic. This isn't to say that Ubuntu's error messages are necessarily better, however.
