![Screenshot from 2024-05-07 17-18-04](https://github.com/Zakaria-Farahi/SOHO-Network/assets/124200547/55c6b63b-586e-42f9-9afc-253b25b6cfe1)


Base Network : 192.168.1.0

No. subnets = 4

No. Sub = 2^n

n = 2

| Subnet ID | Subnet Address | Host Address Range | Broadcast Address |
| --- | --- | --- | --- |
| 1   | 192.168.1.0 | 192.168.1.1 - 192.168.1.62 | 192.168.1.63 |
| 2   | 192.168.1.64 | 192.168.1.65 - 192.168.1.126 | 192.168.1.127 |
| 3   | 192.168.1.128 | 192.168.1.129 - 192.168.1.190 | 192.168.1.191 |
| 4   | 192.168.1.192 | 192.168.1.193 - 192.168.1.254 | 192.168.1.255 |

### Configure Vlans



Switch(config)#int range fa0/8-10: This command enters configuration mode for a range of interfaces on the switch. Specifically, it's configuring interfaces FastEthernet 0/8 to 0/10.

Switch(config-if-range)#switchport mode access: This command sets the mode of the interfaces to access mode. Access mode is typically used when the switch port is connecting to an end device rather than another switch.

Switch(config-if-range)#switchport access vlan 30: This command assigns VLAN 30 to the specified range of interfaces. VLANs are used to segment network traffic.

### Add a password to the wireless Access point

![Screenshot from 2024-05-06 21-36-06](https://github.com/Zakaria-Farahi/SOHO-Network/assets/124200547/bb8d1f1d-3fe0-4261-9b1c-1ae49b4d9609)


### Configure interface fa0/1 to be trunk

![Screenshot from 2024-05-06 21-40-44](https://github.com/Zakaria-Farahi/SOHO-Network/assets/124200547/0cbb3dfa-ed5e-43e0-bca7-c191dcd0c69c)


Trunk mode allows the port to carry traffic for multiple VLANs, facilitating communication between different VLANs or between switches.

### Make the interface of the Router on

![Screenshot from 2024-05-06 21-42-35](https://github.com/Zakaria-Farahi/SOHO-Network/assets/124200547/6e5908fc-b49e-4267-979f-54faf916c958)


### Creating a sub-interface for the router to act as the default gateway

![Screenshot from 2024-05-06 21-46-22](https://github.com/Zakaria-Farahi/SOHO-Network/assets/124200547/c7ef8386-e613-419a-93f9-0a696f84761a)


Router(config)#int g0/0.20: This command enters configuration mode for a subinterface on GigabitEthernet 0/0 with VLAN ID 20. Subinterfaces are virtual interfaces created on a physical interface of a router to allow it to communicate with multiple VLANs or networks.

Router(config-subif)#encapsulation dot1Q 20: This command specifies the encapsulation method for the subinterface. Here, it's using IEEE 802.1Q encapsulation with VLAN ID 20. This allows the router to distinguish between different VLAN traffic on the same physical interface.

Router(config-subif)#ip address 192.168.1.65 255.255.255.192: This command assigns an IP address and subnet mask to the subinterface. In this case, the IP address 192.168.1.65 is assigned with a subnet mask of 255.255.255.192 to the subinterface. This enables the router to communicate with devices in the corresponding network segment.

### Configure DHCP in the Router

![Screenshot from 2024-05-06 21-54-05](https://github.com/Zakaria-Farahi/SOHO-Network/assets/124200547/968b0e66-c0c6-47d4-8435-c798a303149c)


Router(config)#service dhcp: This command enables the DHCP service on the router, allowing it to dynamically assign IP addresses and related network configuration parameters to devices on the network.

Router(config)#ip dhcp pool Admin-pool: This command creates a DHCP pool named "Admin-pool". A DHCP pool is a range of IP addresses from which DHCP can assign addresses to clients.

Router(dhcp-config)#network 192.168.1.0 255.255.255.192: This command defines the network address and subnet mask for the DHCP pool. In this case, it specifies that the DHCP pool will provide IP addresses from the range 192.168.1.0 to 192.168.1.63 with a subnet mask of 255.255.255.192.

Router(dhcp-config)#default-router 192.168.1.1: This command specifies the default gateway (router) that DHCP clients should use. In this case, it sets the default gateway to 192.168.1.1.

Router(dhcp-config)#dns-server 192.168.1.1: This command configures the DNS (Domain Name System) server address that DHCP clients should use. In this case, it sets the DNS server address to 192.168.1.1.

Router(dhcp-config)#domain-name Admin.com: This command sets the domain name that DHCP clients should use for DNS queries. In this case, it sets the domain name to "Admin.com".

### Test Connectivity
![Screenshot from 2024-05-06 22-07-32](https://github.com/Zakaria-Farahi/SOHO-Network/assets/124200547/5aec4c16-0053-43e9-8f5e-8f23b5214b81)
