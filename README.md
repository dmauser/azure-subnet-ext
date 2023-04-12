# Azure Subnet Extension

Lab notes for Subnet Extension feature using Windows Server 2022

Azure side:
1. Deploy script which builds an Hub and two Spokes
2. 

On-Premises side:
1. Hyper-V on Windows 11
2. Two Windows Server VMs (Windows 2019 or 2022)
3. Enable Neste Virtualization on them
4. Create two networks over Hyper-V Switch. LAN and Extended
5. Extended Network uses 172.16.0.0/24
6. Install Hyper-V role on Windows Server 2022 VM
7. Install Windows Admin Center

References:
https://learn.microsoft.com/en-us/azure/virtual-network/subnet-extension

https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/azure/azure-extended-network

https://learn.microsoft.com/en-us/virtualization/hyper-v-on-windows/user-guide/nested-virtualization

https://www.hciharrison.com/azure-stack-hci/azure-extended-networks/

Alternatives:
https://github.com/microsoft/Azure-LISP


To do:
- Remove Public IP from All VMS (update JSON) + Bastion
- Automate part of the Windows 2022 Extended Subnet portion.
- 
- 