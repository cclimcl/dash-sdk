# Setting Up d.ASH VPN

This section of the d.ASH SDK documentation provides details about setting up the d.ASH VPN. Information in this section includes compiling, and testing.
link: https://kifarunix.com/connect-to-vpn-automatically-on-ubuntu-20-04-18-04/

### ^^Setting Up VPN Onboard Computer^^

To start, you will need to configure the VPN configuration file - `client.ovpn` which can be found under the folder `.data/vpn/client.ovpn`. You will need to change the local paths as well as the file names for `ca`, `cert`, and `key`:

cd .data/vpn/

``` python3
sudo apt install network-manager-openvpn network-manager-openvpn-gnome openvpn openvpn-systemd-resolved -y
```

Copy 4 files to /etc/openvpn/client folder
```
ca
cert
key
```

rename client.ovpn to client.conf
```
mv client.ovpn client.conf
cd \etc\openvpn\client
```



Test if it works:
``` python3
systemctl start openvpn-client@client.service
```

# doesn’t work —> error else no print

Now, to check your VPN status, enter the following command: 
``` python3 
systemctl status openvpn-client@client.service
```
If successful, you should be able to see the status `Initialization Sequence Completed`.

``` python3
sudo systemctl enable openvpn-client@client.service
```

### ^^Setting Up VPN Remotely^^

Remember to use a separate login credential from the robot credentials as at any point in time, there can only be one active user session.


Fistly, download [OpenVPN Connect](https://openvpn.net/client-connect-vpn-for-windows/).

Then, click on the _'Import from File'_ tab and drag-and-drop the client.ovpn file located in ``


Final test between two: ping 

