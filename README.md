# map_ubuntu_drive_to_windows
This notes tells you how to map your ubuntu drive to windows machine for easy access

## First, you need to check samba is installed:
``` sudo apt upate ```
```sudo apt install samba```
## next, you need to config he samba setup:
### go to the config file path
``` sudo vim /etc/samba/smb.conf ```
### add something like at the end of the file:
```
[SharedDrive]
        path = /path/to/shared/folder
        available = yes
        valid users = xiaz9n
        read only = no
        browsable = yes
        public = yes
        writable = yes
```
## Then, add a samba user:
```
  sudo smbpasswd -a username
```
## Restart Samba service
```
sudo systemctl restart smbd
```
## open firewall (if needed)
```
sudo ufw allow samba
```
## Now on windows client, do:
```
\\server_ip\shared_drive
shared_drive: should be the same as the name in the square bracket
```
