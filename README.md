# create-samba-share on ubuntu 20.04

Ubuntu 20.04

```
sudo apt install wget git curl htop cifs-utils samba -y
sudo addgroup smbgroup
sudo adduser Joannes
sudo smbpasswd -a Joannes
sudo smbpasswd -e Joannes
sudo mkdir -p /samba/protected
cd /samba/
sudo chown -R root:smbgroup protected
sudo chmod -R 0770 protected
sudo nano /etc/samba/smb.conf
```
Now scroll down to the bottom, and add the following lines:

```
[Protected]
  path = /samba/protected
  valid users = @smbgroup
  guest ok = no
  writable = yes
  browsable = yes
```

Save your changes, and restart the samba service.

```
sudo service smbd restart
```
