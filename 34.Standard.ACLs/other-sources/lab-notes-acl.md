## ACL Lab

#### Requirements

* Verify traffic coming from clients network is from expected addressing range, or deny if not
* Ensure devices in DMZ can send responses if interrogated for web (HTTP/S)
* Ensure devices in DMZ can make HTTP/s and DNS requests to external devices
* Allow traffic coming from outside to enter the network only if it is a response for a request originated from the inside
* Allow ICMP replies to come in
* Ensure that external devices can reach only the public webserver 10.0.2.1
* Show the 'hit' count for denied traffic

#### Configuring Access Lists - How to Construct a Policy

(Policy = Access List)

When creating a policy, it is desirable to end with the cleanest possible set of rules. To do this a true understanding of the requirements is needed. It also needs to be evaluated as to where to apply the policies. This can completely change how the policy works, so both the rules and position need to be planned.

The two common places for access lists: **close to the source** and **close to the destination**. These two concepts rely on the fact that traffic must have a source and destination IP address.

#### Close to the Source

If the policy is applied close to the source it is possible to block traffic before it enters the network and wastes bandwidth for no reason. This is a clear benefit but very specific rules need to be created that include destination addresses. Without this, potentially a lot of traffic will be restricted that should be permitted.

Since a **Standard Access List** does not consider the destination address, nor any Layer 4 information, it cannot work with this approach. 

A Standard Access List can only verify if the **Source IP** is in the expected IP range. Applying a policy in this way would require many different routers to have the policy, increasing administrative burden.

#### Close to the Destination

If the policy is applied close to the destination, it is possible to consider only the source address in a standard access list. As the traffic is already at the destination, we know it was for this network as a designation. The destination is implicit, but ports still cannot be verified. This allows a more centralized management system as the lists only need to go in a few points.








