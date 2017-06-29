# Azure-IKEv2-VPN

the configuration to use IKEv2 on Cisco ASA to Azure

[CiscoASA-ike2.txt](ASA-ikev2.txt) Cisco ASA IKEv2 configuration

## Debug and troubleshooting Infomation
debug crypto ikev2 platform 5 - debug phase 1 (ISAKMP SA`s)
debug crypto ikev2 protocol 5 -  debug phase 1 (ISAKMP SA`s)
debug crypto ipsec - debug phase 2 (IPSEC SA`s)
show crypto ikev2 sa - show phase 1 SA`s
show crypto ipsec sa - show phase 2 SA`s