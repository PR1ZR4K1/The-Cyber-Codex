2024/11/05 15:42
Status: #idea
Tags:

# Wireless Infrastructure Facts

An infrastructure network uses a wireless access point, often called a WAP or AP.

This lesson covers the following topics:

- Enterprise wireless network
- Wireless network components
- Wireless identification tools

## Enterprise Wireless Network

The following diagram shows a sample enterprise wireless network operating in infrastructure mode.

![An enterprise wireless network operating in infrastructure mode](https://cdn.testout.com/_version_7024/ccna2020v7-en-us/en-us/resources/text/t_wl_infra_ccna7/in_wires.jpg)

## Wireless Network Components

The various components of a wireless network are described in the following table.

|Component|Description|
|---|---|
|Station (STA)|An STA is a wireless NIC in an end device such as a laptop or wireless PDA. STA often refers to the device itself, not just the NIC.|
|Access Point (AP)|An AP, sometimes called a wireless AP (WAP), is the device that coordinates all communications between wireless devices, as well as the connection to the wired network. It acts as a hub on the wireless side and a bridge on the wired side. It also synchronizes the stations within a network to minimize collisions.|
|Basic Service Set (BSS)|A BSS, also called a cell, is the smallest unit of a wireless network. All devices in the BSS can communicate with each other. The devices in the BSS depend on the operating mode.<br><br>- In an ad hoc implementation, each BSS contains two devices that communicate directly with each other.<br>- In an infrastructure implementation, the BSS consists of one AP and all its associated STAs.<br><br>All devices within the BSS use the same radio frequency channel to communicate.|
|Independent Basic Service Set (IBSS)|An IBSS is a set of STAs configured in ad hoc mode.|
|Extended Service Set (ESS)|An ESS consists of multiple BSSs with a distribution system (DS). The graphic above is an example of an ESS. In an ESS, BSSs that have an overlapping transmission range use different frequencies.|
|Distribution System (DS)|The DS is the backbone or LAN that connects multiple APs (and BSSs) together. The DS allows wireless clients to communicate with the wired network and with wireless clients in other cells.|

## Wireless Identification Tools

Wireless networks use the following tools for identification.

|Identifier|Description|
|---|---|
|Service Set Identifier (SSID)|The SSID, also called the network name, groups wireless devices together into the same logical network.<br><br>- All devices on the same network (within the BSS and ESS) must have the same SSID.<br>- The SSID is a 32-character value that is inserted into each frame. The SSID is case sensitive.<br>- The SSID is sometimes called the ESSID (extended service set ID) or the BSSID (basic service set ID). In practice, each term means the same thing; however, they are technically different.<br><br>Using the term BSSID to describe the SSID of a BSS is technically incorrect.|
|Basic Service Set Identifier (BSSID)|The BSSID is a 48-bit value that identifies an AP in an infrastructure network or an STA in an ad hoc network. The BSSID allows devices to find a specific AP within an ESS that has multiple access points. STAs use it to keep track of APs as they roam between BSSs. The BSSID is the MAC address of the AP and is set automatically.<br><br>Do not confuse the BSSID with the SSID. They are not the same thing.|





---
# References

- [[Wireless Architecture Facts]]