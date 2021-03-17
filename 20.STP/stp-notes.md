# STP revision

Spanning Tree is IEEE 802.1D
There must be one designated port per collision domain

* 3 fields of STP Bridge ID:
	- Bridge Priority - 4 bits
	- Extended System ID - 12 bits
	- MAC Address - 48 bits

* STP root port selection:
	- lowest bridge ID
	- lowest neighbor bridge ID
	- lowest neighbor port ID

* Interface speed costs:
	- Speed: 10 mbps  = cost: 100
	- Speed: 100 mbps = cost: 19
	- Speed: 1 Gbps	  = cost: 4
	- Speed: 10 Gbps  = cost: 2
