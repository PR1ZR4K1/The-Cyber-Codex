2024/11/06 02:43
Status: #idea
Tags:

# Enterprise Wireless Facts

When implementing a wireless network, you should use the appropriate equipment for the type of deployment. The equipment used in an enterprise wireless network is very different from the equipment used in homes or in small businesses.

This lesson covers the following topics.

- Wireless networks for small business
- Wireless networks for the enterprise

## Wireless Networks for Small Business

Wireless networks for small business typically use a consumer-grade access point that combines many functions into a single device.

These devices work reasonably well in small environments. However, they have very limited capacity, typically supporting a maximum of 5–10 wireless clients at a time. If you connect more clients than this, the bandwidth of the entire wireless network is severely impacted.

## Wireless Networks for the Enterprise

In a larger deployment, you must use high-end equipment designed to support a large number of users. Commonly implemented enterprise deployments are described in the table below:

|Deployment Model|Description|
|---|---|
|Independent access points|In the early days of wireless networking, large organizations implemented independent access points through their facilities. Each AP stood alone, providing separate wireless networks by using its own independent configuration. Independent APs offered limited mobility and were difficult to manage. To enable roaming, network administrators had to configure all access points in the network:<br><br>- With the same SSID.<br>- To use the same channel.<br>- To function on the same IP subnet.<br><br>Otherwise, a mobile device had to get a new IP address every time it moved to a different AP. Changing IP addresses disrupts connectivity.|
|Hub-and-spoke infrastructure|In a hub-and-spoke configuration, a wireless controller is connected to all APs through wired links. The individual APs contain very little embedded intelligence and are sometimes referred to as lightweight access points (LWAPs). The wireless controller:<br><br>- Manages all of the APs that are connected to it. Configuration changes are made once on the controller and are then pushed out to all connected APs.<br>- Provides (typically) DHCP services to dynamically assign IP addressing information to wireless clients.<br>- Connects the wireless network to the internal wired network.<br>- Routes wireless traffic from the wireless network to the internal wired network (and vice versa).<br><br>The hub-and-spoke infrastructure is efficient and allows for large wireless networks. However, the controller itself becomes a bottleneck. All wireless data must pass through the controller, even if it is destined for a wireless host on the same wireless network. The APs are not able to communicate directly with each other. They can communicate only with the wireless controller. If the controller goes down, the entire wireless network ceases to function even if the APs remain functional.|
|Distributed wireless mesh infrastructure|Newer wireless networks can be deployed using a distributed wireless mesh architecture. These networks still use a controller, but move some of the network intelligence from the controller out to the individual APs. In this configuration, the controller is no longer a bottleneck. The APs are smart enough to communicate directly with each other to create efficient data paths for network traffic.<br><br>For example, if one wireless host needs to send data to another wireless host, the data moves from AP to AP using wireless links until it reaches the destination host. The controller is still used to manage, direct, and scale the network, but the work of moving data as efficiently as possible through the wireless LAN is done by the individual APs.<br><br>Because the links are wireless instead of wired, the APs can quickly re-associate themselves with a different wireless controller if the primary controller becomes unavailable for some reason. Many vendors allow you to configure each AP with primary, secondary, and tertiary wireless controllers to provide a high degree of redundancy.<br><br>As with the hub-and-spoke architecture, a wireless controller in a distributed mesh deployment is usually the gateway to the wired network. It routes data from the wireless network to the wired network, and vice versa. For example, on Cisco wireless equipment, the lightweight access point protocol (LWAPP) is used to route frames back and forth between the wireless network and the wired LAN.|
|Wireless bridges|Wireless bridges are used to connect wired or wireless networks together. You can create a wireless link between two buildings with a wireless bridge. Using directional antennae, a wireless signal can be transmitted directly between two buildings, connecting both LANs together. Because the wireless link is a bridge, only the frames addressed to a host on the remote LAN are forwarded across the link. Locally addressed frames remain on the local LAN.|





---
# References
