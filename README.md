# Fixing-Unsupported-file-apt-error
Solution for "Unsupported file package.deb" error in command line

When you see this words in command line it means that some parts of your apt package are corrupted.
There is two way  to solve this problem.

1. Run dpkg -i /path/to/deb/file
It will work because dpkg is dependency free.

2. Another way is to repair your apt installer. I found tons of command line solutions on the internet, but 
none of them where helpful. I start searching again and finally realized that corrupted package is 
libapt-pkg 5.0 (package managment runtime library). 
So, there is working solution. 

a) Open Synaptic package manager.

b) Select "apt" and "libapt-pkg 5.0" packages and reinstall them.

c) From the command line run "apt clean" or "apt-get clean"

d) Close Synaptic package manager. If you leave Synaptic open it can block "apt". You can use only one package manager at the same time. 
Check if "apt" is working now. 

After manipulation with Synaptic package manager you can get errors  when trying to install package with "apt": "Could not get lock /var/cache/apt/archives/lock open. Resource temporarily
unavailable" and "Unable to lock directory var/cache/apt/archives". 
In this case you need to check if there is an instance of "apt" command running. If your machine under remote control
(you never know:) somebody can use terminal on it's own computer and block your actions. 

Check output of "ps" command:

ps aux | grep -i apt

Kill strange processes:

kill -HUP ID (PID)

That's all! Hope it will help you to get your "apt" installer working again.




