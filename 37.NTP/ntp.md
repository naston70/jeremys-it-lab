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











