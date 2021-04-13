## OSPF Advanced 

* OSPF routers identify themselves using an OSPF Router ID which is in the form of an IP address 
* This will default to being the highest IP address of any loopback interfaces configured on the router, or the highest other IP address if a loopback doesnt exist
* Loopback interfaces never go down so the router ID will not change
* You can manually specify the Router ID
* Best practice is to use a Loopback or manually set the Router ID 

