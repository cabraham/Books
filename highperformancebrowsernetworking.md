# [High Performance Browser Networking](https://hpbn.co/)

Latency
: The time from the source sending a packet to the destination receiving it

Bandwidth
: Maximum throughput of a logical or physical communication path

## Components of Latency

Propogation delay
: Amount of time required for a message to travel from the sender to receiver, which is a function of distance over speed with which the signal propagates.

Transmission delay
: Amount of time required to push all the packet’s bits into the link, which is a function of the packet’s length and data rate of the link.

Processing delay
: Amount of time required to process the packet header, check for bit-level errors, and determine the packet’s destination.

Queueing delay
: Amount of time the packet is waiting in the queue until it can be processed.


In typical long-distance network traffic, data is not being transmitted along a simple fiber-optic circuit but many pieces of hardware in between.  Each *hop* adds additional routing, processing, queueing, and transmission delays. 


> 📝Content delivery network (CDN) services address latency by keeping the content physically closer to the client, which reduces the propogation time of all the data packets.  


## Last-Mile Latency

The last few hops to connect to your home goes through a number of steps to get through the ISP.  

> Last-mile latencies can vary wildly between ISP's due to the deployed technology, topology of the network, and even the time of day.

> 📝Latency, not bandwidth, is the performance bottleneck for most websites.

