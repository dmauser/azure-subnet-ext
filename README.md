# Azure Subnet Extension

Lab notes for Subnet Extension feature using Windows Server 2022

### Azure side

Deploy script which builds an Azure VNET with VPN Gateway and three VMs.

### On-Premises side

1. Hyper-V on Windows 11/Windows Server 2022
2. You should have a total of three networks for this solution via Hyper-V Switch:
 - External (for VPN connectivity)
 - LAN
 - Extended
1. Two Windows Server VMs (Windows Server 2022) - One is the LAN Router/VPN Server
1. Two other Windows or Linux VMs. One in the LAN and another in the Extended Network.

#### LAN Router/VPN Server configuration

- Install three NICs (External, LAN and Extended)

#### Onprem-winnva VM:

- Expose two NICs (one for LAN and another for Extended network)
- Install Hyper-V role on Windows Server 2022 VM
- Enable Nested Virtualization

## Solution considerations

- Routing will be asymmetric​
- If you have a firewall between Azure and On-premises: ​
   - Disable sequence number randomization ​
   - Enable TCP state bypass​
   - Require UDP port 4789 open both directions​

​- MTU reduced due to VXLAN overhead​
- Broadcasts aren’t going to broadcast (can’t bring your own DHCP, PXE, etc)
- ​The first three addresses are reserved in Azure subnets​
- Azure Virtual Network Router requires the first address in the subnet
- ​A slight increase in Latency and throughput may be reduced to ~1Gbps​
- One appliance pair required per subnet must always be running​
- Additional steps may be required if using some form of SDN on-prem

References:
https://learn.microsoft.com/en-us/azure/virtual-network/subnet-extension

https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/azure/azure-extended-network

https://learn.microsoft.com/en-us/virtualization/hyper-v-on-windows/user-guide/nested-virtualization

https://www.hciharrison.com/azure-stack-hci/azure-extended-networks/

Alternatives:
https://github.com/microsoft/Azure-LISP

