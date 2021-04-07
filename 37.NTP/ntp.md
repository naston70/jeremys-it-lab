## NTP

- All devices have an internal clock
- In Cisco you can view the time with ```show clock```
- If you use ```show clock detail``` you will see the time source; the hardware calendar is the default time source. If an * is present before the time this indicates the time is not considered authoritative
- The internal hardware clock of a device will drift over time, so it is not the default time source
- From a CCNA perspective the most important reason to have accurate time is for viewing logs

#### Manual Time Configuration

```clock set
```
To configure the time and use ```show clock detail``` to confirm changes. This will also display the time source as user 

* Although the hardware calendar is the default time source, the hardware clock and software clock are seperate and can be configured easily

#### Hardware Clock Configuration

- Using the ```calender set``` command, the hardware calendar can be manually configured.
- Typically the clock and the calendar should be synchronized
- Use the ```clock update-calendar``` to sync the calendar to the clocks time
- Use ```clock read-calendar``` to sync the clock to the calendars time

#### Configuring the Time Zone

- You can read the time zone with the ```clock timezone``` command

Also the daylight savings can be configured to change automatically

```clock summer-time recurring name start end [offset]
```

## Network Time Protocol - NTP

 * Manually configuring time on devices is not scalable
 * The manually configured time on clocks will drift
 * NTP allows automatic syncing of time over a network
 * NTP clients request the time from NTP servers
 * A device can be an NTP server and client at the same time
 * NTP allows accuracy within 1 millisecond if the NTP server is on the same LAN, or within 50 milliseconds if connecting to the NTP server over a WAN
 * Some NTP servers are 'better' than others. The 'distance' of an NTP server from the original reference clock is called stratum
 * NTP uses port 123 UDP

#### Reference Clocks

- A reference clock is usually a very accurate time device like an atomic clock or a GPS clock
- Reference clocks are stratum 0 within NTP hierarchy
- NTP servers directly connected to reference clocks are stratum 1

Reference clocks are stratum 0
* Stratum 1 NTP servers get their time from reference clocks
* Stratum 2 NTP servers get their time from stratum 1 NTP servers
* Stratum 3 NTP servers get their time from stratum 2 NTP servers
* Stratum 15 is considered the max. Anything above is considered unreliable
* Devices can also peer with devices at the stratum to provide a more accurate time.
* This is called 'symmetric active mode'

Cisco devices can operate in three NTP modes:
    - Server mode
    - Client mode
    - Symmetric active mode

An NTP client can sync to multiple servers

NTP servers which get their time from reference clocks are know as **primary servers**

NTP servers which get their time from other NTP servers are called **secondary servers.** They operate in server mode and client mode at the same time.

#### NTP Configuration 

Add NTP servers using:
```ntp server [ip_address]
```
Adding [prefer] keyword to give one priority (if adding more than one server)

```show ntp associations
```
Shows details of the NTP servers on the device (address, ref clock, etc)

```show ntp status
```
Gives further information on NTP. If a server begins synchronizing from another server it will automatically become an NTP server itself with a stratum level 1 higher. Other devices can now synchronize to the device.

NTP uses only the UTC timezone. A device must be configured to the appropriate timezone.

Using the command ```ntp update-calendar``` after adding the NTP servers, configures a device to update the hardware clock (calendar) with the time learned via NTP.
This is important as the hardware clock tracks the date and time on the device even if it restarts or power is lost etc. When the device is restarted the hardware clock is used to initialize the software clock. 










