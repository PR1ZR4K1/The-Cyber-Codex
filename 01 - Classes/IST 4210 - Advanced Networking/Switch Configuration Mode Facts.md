2024/09/18 15:24
Status: #idea
Tags:

# Switch Configuration Mode Facts

A switch has different configuration modes, including interface configuration, VLAN configuration tasks, and terminal line parameter configuration.

The following graphic illustrates some of the configuration modes of the switch:

![A diagram showing the levels of the various switch configuration modes.](https://cdn.testout.com/_version_7024/ccna2020v7-en-us/en-us/resources/text/t_swi_mode_ccna7/swi_mode.jpg)

The following table describes some of the configuration modes of the switch.

|Mode|Details|CLI Mode Prompt|
|---|---|---|
|Interface configuration|The switch has multiple interface modes depending on the physical (or logical) interface type. For this course, you should be familiar with the following switch interface modes:<br><br>- Ethernet (10 Mbps Ethernet)<br>- FastEthernet (100 Mbps Ethernet)<br>- GigabitEthernet (1 GB Ethernet)<br>- VLAN<br><br>The VLAN interface configuration mode is used to configure the switch IP address and other management functions. It is a logical management interface configuration mode, instead of a physical interface configuration mode as used for the FastEthernet and GigabitEthernet ports.|Switch(config-if)#|
|Config-vlan|Details of the config-vlan mode include the following:<br><br>- You can use the config-vlan mode to perform all VLAN configuration tasks.<br>- Changes made in vlan mode take place immediately.<br><br>Do not confuse the config-vlan mode with the VLAN interface configuration mode.|Switch(config-vlan)#|
|Line configuration|Use this mode to configure parameters for the terminal line, such as the console, Telnet, and SSH lines.|Switch(config-line)#|





---
# References

- [[Switch Configuration]]