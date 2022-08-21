# DNSOverTLS

### Install DOG

```bash
mkdir dog && cd dog
VER=$(curl -s https://api.github.com/repos/ogham/dog/releases/latest|grep tag_name|cut -d '"' -f 4|sed 's/v//')
wget https://github.com/ogham/dog/releases/download/v$VER/dog-v$VER-x86_64-unknown-linux-gnu.zip
sudo apt install libssl
unzip dog-*-x86_64-unknown-linux-gnu.zip
sudo cp bin/dog /usr/bin/
```

# Install DNS Over TLS Linux
### Copy resolved.conf 
```bash
sudo cp /etc/systemd/resolved.conf /etc/systemd/resolved.conf.backup
#Buka dan Copas File resolved.conf
#Restart systemd-resolved
sudo systemctl restart systemd-resolved
```

# Mengkonfigurasi NetworkManager
### Langsung Copy Saja Dari File saya 
```bash
cp 01-use-systemd-resolved.conf /etc/NetworkManager/conf.d/
```
# Restart NetworkManager
```bash
sudo systemctl restart  NetworkManager
```
# Silahkan REBOOT

### CHECKING
```bash
resolvectl status
```
### OUTPUT
```bash
#  DNSOverTLS setting: yes ---> DNS over TLS aktif                 
#      DNSSEC setting: yes ---> DNSSEC aktif 
#  Current DNS Server: 1.0.0.1 ---> DNS server saat ini aktif digunakan            
#         DNS Servers: 1.1.1.1              
#                      1.0.0.1  
```

### CHECK VIA WEB BROWSER
```bash
https://1.1.1.1/help
```
### MAKA HASILNYA SEPERTI LINK DIBAWAH
```bash
https://1.1.1.1/help#eyJpc0NmIjoiWWVzIiwiaXNEb3QiOiJZZXMiLCJpc0RvaCI6Ik5vIiwicmVzb2x2ZXJJcC0xLjEuMS4xIjoiWWVzIiwicmVzb2x2ZXJJcC0xLjAuMC4xIjoiWWVzIiwicmVzb2x2ZXJJcC0yNjA2OjQ3MDA6NDcwMDo6MTExMSI6Ik5vIiwicmVzb2x2ZXJJcC0yNjA2OjQ3MDA6NDcwMDo6MTAwMSI6Ik5vIiwiZGF0YWNlbnRlckxvY2F0aW9uIjoiU0lOIiwiaXNXYXJwIjoiTm8iLCJpc3BOYW1lIjoiQ2xvdWRmbGFyZSIsImlzcEFzbiI6IjEzMzM1In0=
```
## License
[MIT](https://choosealicense.com/licenses/mit/)
