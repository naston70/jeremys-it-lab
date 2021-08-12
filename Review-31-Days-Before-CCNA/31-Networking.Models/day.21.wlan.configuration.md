## WLAN Configuration

#### Exam Topics

- Describe AP and WLC management access connections (Telnet, SSH, HTTP, HTTPS, console, TACACS+/RADIUS)

- Configure the components of a wireless LAN access for client connectivity using GUI only such as WLAN creation, security settings, QoS profiles, and advanced WLAN settings

- Configure WLAN using WPA2 PSK using the GUI

## Logging into a Cisco WLC

In order to configure a WLC, access is required. The WLC requires an initial configuration and a management IP address before you can access it with a web browser through HTTP or HTTPS. The initial configuration requires a console connection. The WLC can also be further configured from the command-line interface using Telnet or SSH. The CCNA focuses on GUI access to the WLC.

The Network Summary page is a dashboard that provides a quick overview of the number of configured wireless networks, associate access points and active clients.

#### Network Summary Dashboard

In the menu on the left of the network summary page click **Access Points** to view an overall picture of AP system information and performance.
Click **Advanced** to access the advanced Summary page. From here you can access all the features of the WLC.

## Configuring a WLC with a WLAN

You can configure a WLAN directly on the Cisco 3504 Wireless Controller so that it serves as an AP for wireless clients. However, a WLC is more commonly used in enterprise networks to manage a number of AP's

#### Configuring a Radius Server

An enterprise WLAN typically uses a RADIUS server for user and device authentication before allowing wireless clients to associate with an AP. To configure the WLC with the RADIUS server information:

1. Click **Security** tab > **RADIUS** > **Authentication** to navigate to the correct screen.

2. Click **New** to add the RADIUS server


#### Configuring a New Interface

Each WLAN configured on the WLC needs its own virtual interface. The WLC has 5 physical ports for data traffic. Each physical port can be configured to support multiple WLANs, each on its own virtual interface. The virtual interface is typically named with a VLAN number and associated to that VLAN. The

1. Create a new interface by clicking: **CONTROLLER > Interfaces > New**

2. Configure an Interface name and VLAN ID, such as 'vlan5' and ID '5', click apply to create the new interface 

3. On the Edit page for the interface, configure the physical port number and IP addressing information 

4. In order to forward DHCP messages to a dedicated DHCP server, configure the DHCP server address 

5. Scroll to the top and click **Apply** and **OK** on the warning message

6. To verify the newly configured virtual interface, click **Interfaces.** The new 'vlan5' interface is now shown in the list of interfaces with its IPv4 address. 

#### Configuring a WPA2 Enterprise WLAN 

