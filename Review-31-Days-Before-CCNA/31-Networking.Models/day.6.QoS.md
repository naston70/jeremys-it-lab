## QoS

###### Exam Topic

- Explain the PHB for QoS such as classification, marking, queuing congestion, policing shaping

#### QoS

Normal default operation for switches and routers is to process frames and packets in the order in which they are received. FIFO does not discriminate between traffic types

QoS tools are used to classify traffic types based on the four following characteristics

- Latency: Latency, or delay, is the amount of time it takes for data to be sent to the receiver. QoS tools can reduce the delay for time-sensitive packets, such as voice and video
- Jitter: Jitter is the variance in the delay of packets. QoS tools can even out the delay of packets to improve end user experience
- Loss: Loss refers to the number of lost messages, usually as a percentage of the packets sent. QoS tools reduce packet loss, especially for time sensitive traffic
- Bandwidth: Bandwidth is a measure of the amount of data an interface can send every second. QoS tools can manage which traffic type gets to use the bandwidth next and how much of the bandwidth each type of traffic gets over time. 

#### Characteristics of Major Traffic Types

###### VOICE:
* Smooth
* Benign
* Drop sensitive
* Delay sensitive
* UDP priority

- One-Way Requirements
    * Latency < 150 ms 
    * Jitter  < 30 ms 
    * Loss    < 1% 
    * Bandwidth (30-128 kbps)

###### VIDEO:
* Bursty
* Greedy
* Drop sensitive
* Delay sensitive
* UDP priority

- One-Way Requirements
    * Latency < 200 - 400 ms 
    * Jitter  < 30 - 50 ms 
    * Loss    < 0.1 - 1%
    * Bandwidth (384 kbps - 20+ Mbps)

#### Overview of QoS tools








