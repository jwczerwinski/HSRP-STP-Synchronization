# HSRP-STP-Synchronization

<h2>Description</h2>
Confgiure HSRP on DSW1/DSW2 and synchronize with STP within separate VLANs.

<h2>Environments Used </h2>

- <b>Cisco Packet Tracer</b> (2.2.43) <br />

- <b>Cisco IOS Denali, Catalyst L3 Switch Software, Version 16.3.2</b> <br />

[Software Configuration Guide](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst3650/software/release/16-3/configuration_guide/b_163_consolidated_3650_cg.html)<br />

<h2>Diagram </h2>
<img src="https://i.imgur.com/eYPIcnw.png" height="80%" width="80%" />

<h2>Walk-through:</h2>
Configurations on DSW1 for VLAN 10: STP VLAN 10 root primary, interface VLAN 10 - HSRP group #10 IP address 10.0.10.254 with priority 105 and preemption. <br />
DSW1(config)#spanning-tree vlan 10 root primary <br />
DSW1(config)#int vlan 10 <br />
DSW1(config-if)#standby version 2 <br />
DSW1(config-if)#standby 10 ip 10.0.10.254 <br />
DSW1(config-if)#standby 10 priority 105 <br />
DSW1(config-if)#standby 10 preempt <br />
Configurations on DSW2 for VLAN 10: STP VLAN 10 root secondary, interface VLAN 10 - HSRP group #10 IP address 10.0.10.254 with priority 95 and preemption. <br />
DSW2(config)#spanning-tree vlan 10 root secondary
DSW2(config)#int vlan 10
DSW2(config-if)#standby version 2
DSW2(config-if)#standby 10 ip 10.0.10.254
DSW2(config-if)#standby 10 priority 95
DSW2(config-if)#standby 10 preempt
Follow example for VLAN 20. Verify results wtih commands 'show standby' and 'show spanning-tree'. <br />
<img src="https://i.imgur.com/EgOihGL.png" height="80%" width="80%" />
<img src="https://i.imgur.com/NIWpVKW.png" height="80%" width="80%" />
<img src="https://i.imgur.com/l66TaLJ.png" height="80%" width="80%" />
<img src="https://i.imgur.com/Y7L95WV.png" height="80%" width="80%" />
