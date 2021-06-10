# Setting Up d.ASH VPN

This section of the d.ASH SDK documentation provides details about setting up the d.ASH VPN. 

link: https://kifarunix.com/connect-to-vpn-automatically-on-ubuntu-20-04-18-04/

### ^^Setting Up VPN Onboard Computer^^

To start, you will need to configure the VPN configuration file - `client.ovpn` which can be found in the folder `/dash_sdk/vpn`. Firstly, install the packages to configure automatic VPN connection on Ubuntu 18.04 LTS by executing the following command:

``` python3
sudo apt install network-manager-openvpn network-manager-openvpn-gnome openvpn openvpn-systemd-resolved -y
```

This will install an `openvpn` package, which creates a `/etc/openvpn/client/` directory into which you can place the OpenVPN client configuration file. Therefore, you will need to copy `client.ovpn` as well as your d.ASH client folder,into the new open-vpn directory. To do this, execute the following commands:

```
sudo cp -r client.ovpn /etc/openvpn/client/client.conf 
sudo cp -r <client_folder>/ /etc/openvpn/client/
```

Now, you will need to change the paths in `client.conf` found in the directory `/etc/openvpn/client/`. To find the local path by entering `pwd`. Append the directory likewise such that the `PATH` of `client.conf` matches.

For example:
```
cat

```

use `pwd` to find absolute path 



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

