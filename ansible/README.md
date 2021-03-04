# Ansible-Onboarding

* Open PowerShell as administrator
* Run command `Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux`
* Restart your computer when prompted
* After restart, Open Settings -> Update and Security -> For developers, then select `Developer Mode`
* Open a command prompt and type `bash` then enter, then `y` then enter
* You can now open an Ubuntu shell by either typing bash into command line or clicking the start menu shortcut
* Open an Ubuntu shell
  * Create a username and password which is totally separate from any other credentials (you'll only do this once)
* Run `sudo apt-get update`
* Then, `sudo apt-get upgrade`
* Then, `sudo apt-get update`
* Then, `sudo apt-get install software-properties-common`
* Then, `sudo apt-add-repository ppa:ansible/ansible`
* Then, `sudo apt-get update`
* Then, `sudo apt-get install ansible`
* Then, `sudo apt-get purge openssh-server`
* Then, `sudo apt-get install openssh-server`
* Then, `sudo vim /etc/ssh/sshd_config` then `i` to edit and disallow root login by setting `PermitRootLogin no`  
  Then add a line beneath it that says: `AllowUsers yourubuntuusername`  
  and make sure `PasswordAuthentication yes` to make sure password is used  
  Disable privilege separation by adding/modifying : `UsePrivilegeSeparation no`  
  Finally, hit escape, then type `:wq`, then enter
* Then, `sudo service ssh --full-restart`
  * Remember this command as you have to do this after each time your Ubuntu bash restarts to get Ansible to work  
* In your Ubuntu shell, run `sudo vim /etc/ansible/ansible.cfg`then hit `i` to edit
  * Uncomment the `library` line and set `library = /mnt/c/Users/racf/lib`
  * Add a line `host_key_checking = false`
  * Hit escape, then type `:wq`, then enter
* In File Explorer, create a lib directory under your racf
  * This is where you will store any and all Ansible modules you want to use
* Run `sudo vim /etc/ansible/hosts`, then hit `i` to edit, and add a section like this to the host file:
```sh
[localhost]
127.0.0.1
[localhost:vars]
ansible_user=[your Ubuntu username]
ansible_ssh_pass=[your Ubuntu password]
```
<br><br/>  
* Within WSL, there is a unique linux filesystem that is created.  Type `cd /mnt/c/Users/racf` you get access to all  
  of your files
