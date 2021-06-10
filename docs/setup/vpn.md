# Setting Up d.ASH VPN

Two separate login credentials are required for two seperate VPN connectiosn - one for the robot onboard computer and one for the remote client. This section of the d.ASH SDK documentation provides details about setting up the d.ASH VPN. 

---

### ^^Setting Up VPN Onboard Computer^^

To start, you will need to install some packages to configure automatic VPN connection on Ubuntu 18.04 LTS by executing the following command:

``` python3
sudo apt install network-manager-openvpn network-manager-openvpn-gnome openvpn openvpn-systemd-resolved -y
```

This will install an `openvpn` package, which creates a `/etc/openvpn/client/` directory into which you can place the OpenVPN client configuration file. You will need to configure the VPN configuration file - `client.ovpn` which can be found in your vpn folder `/dash_sdk/vpn`. To do so, run the following command:


```
RUN A SCRIPT TO CHANGE PATHS 
```


Now, you will need to copy `client.ovpn` as well as your client folder into the new open-vpn directory. In the `/dash_sdk` directory, execute the following commands:

``` python3
sudo cp client.ovpn /etc/openvpn/client/client.conf 
sudo cp -r <USERNAME>/ /etc/openvpn/client
```

For example, in the directory `/dash_sdk/vpn`, if your client folder is named `dc`, you would run as such, replacing `<USERNAME>` with your client folder name:

``` python3
sudo cp client.ovpn /etc/openvpn/client/client.conf 
sudo cp -r dc/ /etc/openvpn/client
```

To check that your files have been copied and renamed correctly, `cd` into the `/etc/openvpn/client` directory and `ls` to see your list of files. You should have `client.conf` and `<USERNAME>` client folder present:
``` python3
$ cd /etc/openvpn/client
$ ls
client.conf <client_folder>
```

Now, let's test that the VPN service was set up correctly by running the following command:
``` python3
sudo systemctl start openvpn-client@client.service
```

If there is no error print, proceed onto the next step. If you come across a failure, ensure that the path in `client.conf` matches the following format:

```python3
cat \etc\openvpn\client\<USERNAME>\ca.crt
cert \etc\openvpn\client\<USERNAME>\<USERNAME>.crt
key \etc\openvpn\client\<USERNAME>\<USERNAME>.crt
```

Now, to check your VPN status, enter the following command: 
``` python3 
sudo systemctl status openvpn-client@client.service
```
If successful, you should be able to see the status `Initialization Sequence Completed`. Lastly, enable the VPN onboard your computer by executing the following command: 

``` python3
sudo systemctl enable openvpn-client@client.service
```

---

### ^^Setting Up VPN Remotely^^

Remember to use a separate login credential from the robot onboard computer credentials as at any point in time, there can only be one active user session.


Fistly, download [OpenVPN Connect](https://openvpn.net/client-connect-vpn-for-windows/). Then, click on the _'Import from File'_ tab and drag-and-drop the `client.ovpn` file located in `\dash-sdk\vpn\<USERNAME>`.


