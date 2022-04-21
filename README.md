# WSL2-Vagrant-Windows
How to access Vagrant SSH on Windows via WSL2?

If you run `vagrant.exe ssh` you will get an empty output<br />
The solution is to connect to it directly, but we need to expose the ssh port first.<br />
In your "Vagrantfile" add the following file<br />
`config.vm.network "forwarded_port", protocol: "tcp", guest: 22, host: 2222`<br />
<br />
Once this is done  you can run `vagrant.exe reload` to realod the "Vagrantfile".<br />
Once the VM is ready again you can run the following command to SSH:<br />
`ssh -p 2222 -i <private_key> <username>@$(ip route |grep default |cut -f 3 -d ' ')`<br />
<br />
