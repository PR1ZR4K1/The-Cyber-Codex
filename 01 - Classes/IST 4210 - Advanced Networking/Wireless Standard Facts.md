2024/11/05 16:23
Status: #idea
Tags:

# Wireless Standard Facts

The original 802.11 specification operated in the 2.4 GHz range and provided up to 2 Mbps transfer speeds. Since then, additional IEEE subcommittees have further refined wireless networking.

This lesson covers the following topics:

- 802.11n
- 802.11ac
- Wireless network implementation

The following table describes the various wireless standards and their specifications:
![[Pasted image 20241105162427.png]]
## 802.11n

802.11n modified the previous 802.11a (5 GHz) and 802.11g (2.4GHz) standards to increase their potential bandwidth and transmission distance. The following table describes the technologies implemented as part of this modification:

|Technology|Details|
|---|---|
|Multiple-Input, Multiple-Output (MIMO)|MIMO increases bandwidth by using multiple antennas for both the transmitter and receiver.<br><br>A system is described by the number of sending and receiving antennas. The 802.11n specifications allow up to four sending and four receiving antennas. The benefit of adding additional antennas declines as the number increases; going above 3x3 provides a negligible performance increase.|
|Channel bonding|Channel bonding combines two non-overlapping 20 MHz channels into a single 40 MHz channel, resulting in slightly more than double the bandwidth.<br><br>- The 5 GHz range has a total of 23 channels, 12 of which are non-overlapping. This allows for a maximum of 6 non-overlapping bonded (combined) channels.<br>- The 2.4 GHz range has a total of 11 channels, three of which are non-overlapping. This allows for a maximum of 1 non-overlapping channel. For this reason, channel bonding isn't usually practical for the 2.4 GHz range.|
|Frame composition|802.11n changes the frame composition, resulting in increased efficiency of data transmissions due to less overhead.|

When running at 802.11n speeds, 802.11a and 802.11g are considered high throughput (HT) and sometimes referred to as 802.11a-ht and 802.11g-ht.

## 802.11ac

802.11ac increased bandwidth and communication speeds by using the following technologies:

|Technology|Details|
|---|---|
|Multi-user MIMO  <br>(MU-MIMO)|MU-MIMO is an enhancement to MIMO that allows multiple users to use the same channel.<br><br>In addition to adding MU-MIMO, 802.11ac doubled the number of MIMO radio streams from four to eight.|
|Channel bonding|Channel bonding is used to combine even more channels in the 5 GHz band, allowing for up to 160 MHz wide channels.<br><br>Even though 160 MHz wide channels are supported, most 802.11ac networks use 80 MHz wide channels.|
|Frame composition|802.11ac added four fields to the wireless frame, which identify the frame as very high throughput (VHT).|

## Wireless Network Implementation

The following table describes wireless network implementation considerations:

|Consideration|Description|
|---|---|
|Speed and signal distance|When implementing the wireless network, keep in mind the following concerning signal distance and speed.<br><br>- Transmission speeds are affected by distance, obstructions (such as walls), and interference.<br>- Maximum signal distance depends on several factors, including obstructions, antenna strength, and interference. For example, for communications in a typical environment (with one or two walls), the actual distance would be roughly half of the maximum.<br>- Because transmission speeds decrease with distance, you can either achieve the maximum distance or the maximum speed, but not both.|
|Mixing newer and older devices|Newer devices' ability to communicate with older devices depends on the capabilities of the transmit radios in the access point.<br><br>- Some 802.11n devices are capable of transmitting at either 2.4 GHz or 5 GHz. However, a single radio cannot transmit at both frequencies at the same time.<br>- Most 802.11g devices can transmit using DSSS, CCK, DQPSK, and DBPSK for backwards compatibility with 802.11b devices. However, the radio cannot transmit using both DSSS and OFDM at the same time.<br><br>When you connect a legacy device to the wireless network, all devices on the network operate at the legacy speed. For example, connecting an 802.11b device to an 802.11n or 802.11g access point slows down the network to 802.11b speeds.|
|Dual band access points|A dual band access point can use one radio to transmit at one frequency and a different radio to transmit at a different frequency. For example, you can configure many 802.11n devices to use one radio to communicate at 5 GHz with 802.11a devices, and the remaining radios to use 2.4 GHz to communicate with 802.11n devices. Dual band 802.11a and 802.11g devices are also available.|
|Mixed mode|Be aware of the following when combining clients that use different 802.x standards.<br><br>- When you configure an access point, some configuration utilities use the term mixed mode to designate a network with both 802.11n and non-802.11n clients. In this configuration, one radio transmitter is used for legacy clients, and the remaining radio transmitters are used for 802.11n clients.<br>- Many 802.11n access points can support clients running other wireless standards (802.11a/b/g). When a mix of clients using different standards are connected, the access point must disable some 802.11n features to be compatible with non-802.11n devices. This decreases the effective speed.<br>- Some newer 802.11a and 802.11g devices provide up to 108 Mbps using 802.11n pre-draft technologies (MIMO and channel bonding).|





---
# References
