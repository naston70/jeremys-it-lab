## Quality of Service

##### Quality of Service Models

**Best Effort:** No QoS policies are implemented
**Integrated Services (IntServ):** Resource Reservation Protocol (RSVP) is used to reserve bandwidth per-flow across all nodes in a path
**Differentiated Services (DiffServ):** Packets are individually classified and marked; policy decisions are made independently by each node in a path

##### Terminology

*Per-Hop Behavior:* The individual QoS action performed at each independent DiffServ node 

*Trust Boundary:* Beyond this, inbound QoS markings are not trusted 

*Tail Drops:* Occurs when a packet is dropped because a queue is full 

*Policing:* Imposes an artificial ceiling on the amount of bandwidth that may be consumed; traffic exceeding the policer rate is reclassified or dropped

*Shaping:* Similar to policing but buffers excess traffic for delayed transmission; makes more efficient use of bandwidth but introduces a delay

*TCP Synchronization:* Flows adjust TCP windows sizes in sync, making inefficient use of a link