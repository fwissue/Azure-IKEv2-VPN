# Azure-IKEv2-VPN

access-list metoazure line 1 extended permit ip 10.0.0.0 255.255.0.0 10.1.0.0 255.255.0.0

crypto ikev2 policy 60
 encryption aes-256
 integrity sha384
 group 24
 prf sha384
 lifetime seconds 3600
 
 crypto ipsec ikev2 ipsec-proposal IPSEC-AZURE
 protocol esp encryption aes-256
 protocol esp integrity sha-256
 
group-policy AZURE internal
group-policy AZURE attributes
 vpn-tunnel-protocol ikev2
 
tunnel-group 66.66.66.66 type ipsec-l2l
tunnel-group 66.66.66.66 general-attributes
 default-group-policy AZURE

tunnel-group 66.66.66.66 ipsec-attributes
  ikev2 remote-authentication pre-shared-key xxxxxx
  ikev2 local-authentication pre-shared-key xxxxxx

crypto map dyn-map 10 match address metoazure
crypto map dyn-map 10 set pfs group24
crypto map dyn-map 10 set peer 66.66.66.66
crypto map dyn-map 10 set ikev2 ipsec-proposal IPSEC-AZURE
 
crypto ikev2 enable OUTSIDE

## Debug and troubleshooting Infomation
debug crypto ikev2 platform 5 - debug phase 1 (ISAKMP SA`s)
debug crypto ikev2 protocol 5 -  debug phase 1 (ISAKMP SA`s)
debug crypto ipsec - debug phase 2 (IPSEC SA`s)
show crypto ikev2 sa - show phase 1 SA`s
show crypto ipsec sa - show phase 2 SA`s