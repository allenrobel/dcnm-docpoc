#### AAA_REMOTE_IP_ENABLED

Enable only, when IP Authorization is enabled in the AAA Server

- default: 0
- example: NA
- type: bool

#### AAA_SERVER_CONF

AAA Configurations

- default: 
- example: NA
- type: str

#### ADVERTISE_PIP_BGP

For Primary VTEP IP Advertisement As Next-Hop Of Prefix Routes

- default: 0
- example: NA
- type: bool

#### ADVERTISE_PIP_ON_BORDER

Enable advertise-pip on vPC borders and border gateways only. Applicable only when vPC advertise-pip is not enabled

- default: 1
- example: NA
- type: bool

#### ANYCAST_BGW_ADVERTISE_PIP

To advertise Anycast Border Gateway PIP as VTEP. Effective on MSD fabric Recalculate Config

- default: 0
- example: NA
- type: bool

#### ANYCAST_GW_MAC

Shared MAC address for all leafs (xxxx.xxxx.xxxx)

- default: 2020.0000.00aa
- example: NA
- type: str

#### ANYCAST_LB_ID

Used for vPC Peering in VXLANv6 Fabrics 

- default: 10
- example: NA
- type: int

#### ANYCAST_RP_IP_RANGE

Anycast or Phantom RP IP Address Range

- default: 10.254.254.0/24
- example: NA
- type: str

#### AUTO_SYMMETRIC_DEFAULT_VRF

Whether to auto generate Default VRF interface and BGP peering configuration on managed neighbor devices. If set, auto created VRF Lite IFC links will have Auto Deploy Default VRF for Peer enabled.

- default: 0
- example: NA
- type: bool

#### AUTO_SYMMETRIC_VRF_LITE

Whether to auto generate VRF LITE sub-interface and BGP peering configuration on managed neighbor devices. If set, auto created VRF Lite IFC links will have Auto Deploy for Peer enabled.

- default: 0
- example: NA
- type: bool

#### AUTO_UNIQUE_VRF_LITE_IP_PREFIX

When enabled, IP prefix allocated to the VRF LITE IFC is not reused on VRF extension over VRF LITE IFC. Instead, unique IP Subnet is allocated for each VRF extension over VRF LITE IFC.

- default: 0
- example: NA
- type: bool

#### AUTO_VRFLITE_IFC_DEFAULT_VRF

Whether to auto generate Default VRF interface and BGP peering configuration on VRF LITE IFC auto deployment. If set, auto created VRF Lite IFC links will have Auto Deploy Default VRF enabled.

- default: 0
- example: NA
- type: bool

#### BANNER

Message of the Day (motd) banner. Delimiter char (very first char is delimiter char) followed by message ending with delimiter

- default: 
- example: NA
- type: str

#### BFD_AUTH_ENABLE

Valid for P2P Interfaces only

- default: 0
- example: NA
- type: bool

#### BFD_AUTH_KEY

Encrypted SHA1 secret value

- default: 
- example: NA
- type: str

#### BFD_AUTH_KEY_ID

No description available

- default: 100
- example: NA
- type: int

#### BFD_ENABLE

Valid for IPv4 Underlay only

- default: 0
- example: NA
- type: bool

#### BFD_IBGP_ENABLE

No description available

- default: 0
- example: NA
- type: bool

#### BFD_ISIS_ENABLE

No description available

- default: 0
- example: NA
- type: bool

#### BFD_OSPF_ENABLE

No description available

- default: 0
- example: NA
- type: bool

#### BFD_PIM_ENABLE

No description available

- default: 0
- example: NA
- type: bool

#### BGP_AS

1-4294967295 | 1-65535.0-65535 It is a good practice to have a unique ASN for each Fabric.

- default: 
- example: NA
- type: str

#### BGP_AUTH_ENABLE

No description available

- default: 0
- example: NA
- type: bool

#### BGP_AUTH_KEY

Encrypted BGP Authentication Key based on type

- default: 
- example: NA
- type: str

#### BGP_AUTH_KEY_TYPE

BGP Key Encryption Type: 3 - 3DES, 7 - Cisco

- default: 3
- example: NA
- type: str

#### BGP_LB_ID

No description available

- default: 0
- example: NA
- type: int

#### BOOTSTRAP_CONF

Additional CLIs required during device bootup/login e.g. AAA/Radius

- default: 
- example: NA
- type: str

#### BOOTSTRAP_ENABLE

Automatic IP Assignment For POAP

- default: 0
- example: NA
- type: bool

#### BOOTSTRAP_MULTISUBNET

lines with # prefix are ignored here

- default: #Scope_Start_IP, Scope_End_IP, Scope_Default_Gateway, Scope_Subnet_Prefix
- example: NA
- type: str

#### BROWNFIELD_NETWORK_NAME_FORMAT

Generated network name should be &lt; 64 characters

- default: Auto_Net_VNI$$VNI$$_VLAN$$VLAN_ID$$
- example: NA
- type: str

#### BROWNFIELD_SKIP_OVERLAY_NETWORK_ATTACHMENTS

Enable to skip overlay network interface attachments for Brownfield and Host Port Resync cases

- default: 0
- example: NA
- type: bool

#### CDP_ENABLE

Enable CDP on management interface

- default: 0
- example: NA
- type: bool

#### COPP_POLICY

Fabric Wide CoPP Policy. Customized CoPP policy should be provided when manual is selected

- default: strict
- example: NA
- type: str

#### DCI_SUBNET_RANGE

Address range to assign P2P Interfabric Connections

- default: 10.33.0.0/16
- example: NA
- type: str

#### DCI_SUBNET_TARGET_MASK

No description available

- default: 30
- example: NA
- type: int

#### DEFAULT_QUEUING_POLICY_CLOUDSCALE

Queuing Policy for all 92xx, -EX, -FX, -FX2, -FX3, -GX series switches in the fabric

- default: queuing_policy_default_8q_cloudscale
- example: NA
- type: str

#### DEFAULT_QUEUING_POLICY_OTHER

Queuing Policy for all other switches in the fabric

- default: queuing_policy_default_other
- example: NA
- type: str

#### DEFAULT_QUEUING_POLICY_R_SERIES

Queuing Policy for all R-Series switches in the fabric

- default: queuing_policy_default_r_series
- example: NA
- type: str

#### DEFAULT_VRF_REDIS_BGP_RMAP

Route Map used to redistribute BGP routes to IGP in default vrf in auto created VRF Lite IFC links

- default: extcon-rmap-filter
- example: NA
- type: str

#### DEPLOY

Save and deploy the fabric configuration.

- default: False
- example: NA
- type: bool

#### DHCP_ENABLE

Automatic IP Assignment For POAP From Local DHCP Server

- default: 0
- example: NA
- type: bool

#### DHCP_END

End Address For Switch POAP

- default: 
- example: NA
- type: str

#### DHCP_IPV6_ENABLE

No description available

- default: DHCPv4
- example: NA
- type: str

#### DHCP_START

Start Address For Switch POAP

- default: 
- example: NA
- type: str

#### DNS_SERVER_IP_LIST

Comma separated list of IP Addresses(v4/v6)

- default: 
- example: NA
- type: str

#### DNS_SERVER_VRF

One VRF for all DNS servers or a comma separated list of VRFs, one per DNS server

- default: 
- example: NA
- type: str

#### ENABLE_AAA

Include AAA configs from Manageability tab during device bootup

- default: 0
- example: NA
- type: bool

#### ENABLE_DEFAULT_QUEUING_POLICY

No description available

- default: 0
- example: NA
- type: bool

#### ENABLE_FABRIC_VPC_DOMAIN_ID

(Not Recommended)

- default: 0
- example: NA
- type: bool

#### ENABLE_MACSEC

Enable MACsec in the fabric

- default: 0
- example: NA
- type: bool

#### ENABLE_NETFLOW

Enable Netflow on VTEPs

- default: 0
- example: NA
- type: bool

#### ENABLE_NGOAM

Enable the Next Generation (NG) OAM feature for all switches in the fabric to aid in trouble-shooting VXLAN EVPN fabrics

- default: 1
- example: NA
- type: bool

#### ENABLE_NXAPI

Enable HTTPS NX-API

- default: 1
- example: NA
- type: bool

#### ENABLE_NXAPI_HTTP

No description available

- default: 1
- example: NA
- type: bool

#### ENABLE_PBR

When ESR option is ePBR, enable ePBR will enable pbr, sla sender and epbr features on the switch

- default: 0
- example: NA
- type: bool

#### ENABLE_PVLAN

Enable PVLAN on switches except spines and super spines

- default: 0
- example: NA
- type: bool

#### ENABLE_TENANT_DHCP

No description available

- default: 1
- example: NA
- type: bool

#### ENABLE_TRM

For Overlay Multicast Support In VXLAN Fabrics

- default: 0
- example: NA
- type: bool

#### ENABLE_VPC_PEER_LINK_NATIVE_VLAN

No description available

- default: 0
- example: NA
- type: bool

#### ESR_OPTION

Policy-Based Routing (PBR) or Enhanced PBR (ePBR)

- default: PBR
- example: NA
- type: str

#### EXTRA_CONF_INTRA_LINKS

Additional CLIs For All Intra-Fabric Links

- default: 
- example: NA
- type: str

#### EXTRA_CONF_LEAF

Additional CLIs For All Leafs As Captured From Show Running Configuration

- default: 
- example: NA
- type: str

#### EXTRA_CONF_SPINE

Additional CLIs For All Spines As Captured From Show Running Configuration

- default: 
- example: NA
- type: str

#### EXTRA_CONF_TOR

Additional CLIs For All ToRs As Captured From Show Running Configuration

- default: 
- example: NA
- type: str

#### FABRIC_INTERFACE_TYPE

Numbered(Point-to-Point) or Unnumbered

- default: p2p
- example: NA
- type: str

#### FABRIC_MTU

. Must be an even number

- default: 9216
- example: NA
- type: int

#### FABRIC_NAME

Please provide the fabric name to create it (Max Size 32)

- default: 
- example: NA
- type: str

#### FABRIC_TYPE

The type of fabric.

- default: None
- example: NA
- type: str

#### FABRIC_VPC_DOMAIN_ID

vPC Domain Id to be used on all vPC pairs

- default: 1
- example: NA
- type: int

#### FABRIC_VPC_QOS

Qos on spines for guaranteed delivery of vPC Fabric Peering communication

- default: 0
- example: NA
- type: bool

#### FABRIC_VPC_QOS_POLICY_NAME

Qos Policy name should be same on all spines

- default: spine_qos_for_fabric_vpc_peering
- example: NA
- type: str

#### FEATURE_PTP

No description available

- default: 0
- example: NA
- type: bool

#### GRFIELD_DEBUG_FLAG

Enable to clean switch configuration without reload when PreserveConfig=no

- default: Disable
- example: NA
- type: str

#### HD_TIME

NVE Source Inteface HoldDown Time  in seconds

- default: 180
- example: NA
- type: int

#### HOST_INTF_ADMIN_STATE

No description available

- default: 1
- example: NA
- type: bool

#### IBGP_PEER_TEMPLATE

Speficies the iBGP Peer-Template config used for RR and spines with border role.

- default: 
- example: NA
- type: str

#### IBGP_PEER_TEMPLATE_LEAF

Specifies the config used for leaf, border or border gateway. If this field is empty, the peer template defined in iBGP Peer-Template Config is used on all BGP enabled devices (RRs,leafs, border or border gateway roles.

- default: 
- example: NA
- type: str

#### INBAND_DHCP_SERVERS

Comma separated list of IPv4 Addresses (Max 3)

- default: 
- example: NA
- type: str

#### INBAND_MGMT

Manage switches with only Inband connectivity

- default: 0
- example: NA
- type: bool

#### ISIS_AUTH_ENABLE

No description available

- default: 0
- example: NA
- type: bool

#### ISIS_AUTH_KEY

Cisco Type 7 Encrypted

- default: 
- example: NA
- type: str

#### ISIS_AUTH_KEYCHAIN_KEY_ID

No description available

- default: 127
- example: NA
- type: int

#### ISIS_AUTH_KEYCHAIN_NAME

No description available

- default: 
- example: NA
- type: str

#### ISIS_LEVEL

Supported IS types: level-1, level-2

- default: level-2
- example: NA
- type: str

#### ISIS_OVERLOAD_ELAPSE_TIME

Clear the overload bit after an elapsed time in seconds

- default: 60
- example: NA
- type: int

#### ISIS_OVERLOAD_ENABLE

When enabled, set the overload bit for an elapsed time after a reload

- default: 1
- example: NA
- type: bool

#### ISIS_P2P_ENABLE

This will enable network point-to-point on fabric interfaces which are numbered

- default: 1
- example: NA
- type: bool

#### L2_HOST_INTF_MTU

. Must be an even number

- default: 9216
- example: NA
- type: int

#### L2_SEGMENT_ID_RANGE

Overlay Network Identifier Range 

- default: 30000-49000
- example: NA
- type: str

#### L3VNI_MCAST_GROUP

Default Underlay Multicast group IP assigned for every overlay VRF.

- default: 239.1.1.0
- example: NA
- type: str

#### L3_PARTITION_ID_RANGE

Overlay VRF Identifier Range 

- default: 50000-59000
- example: NA
- type: str

#### LINK_STATE_ROUTING

Used for Spine-Leaf Connectivity

- default: ospf
- example: NA
- type: str

#### LINK_STATE_ROUTING_TAG

Underlay Routing Process Tag

- default: UNDERLAY
- example: NA
- type: str

#### LOOPBACK0_IPV6_RANGE

Typically Loopback0 IPv6 Address Range

- default: fd00::a02:0/119
- example: NA
- type: str

#### LOOPBACK0_IP_RANGE

Typically Loopback0 IP Address Range

- default: 10.2.0.0/22
- example: NA
- type: str

#### LOOPBACK1_IPV6_RANGE

Typically Loopback1 and Anycast Loopback IPv6 Address Range

- default: fd00::a03:0/118
- example: NA
- type: str

#### LOOPBACK1_IP_RANGE

Typically Loopback1 IP Address Range

- default: 10.3.0.0/22
- example: NA
- type: str

#### MACSEC_ALGORITHM

AES_128_CMAC or AES_256_CMAC

- default: AES_128_CMAC
- example: NA
- type: str

#### MACSEC_CIPHER_SUITE

Configure Cipher Suite

- default: GCM-AES-XPN-256
- example: NA
- type: str

#### MACSEC_FALLBACK_ALGORITHM

AES_128_CMAC or AES_256_CMAC

- default: AES_128_CMAC
- example: NA
- type: str

#### MACSEC_FALLBACK_KEY_STRING

Cisco Type 7 Encrypted Octet String

- default: 
- example: NA
- type: str

#### MACSEC_KEY_STRING

Cisco Type 7 Encrypted Octet String

- default: 
- example: NA
- type: str

#### MACSEC_REPORT_TIMER

MACsec Operational Status periodic report timer in minutes

- default: 5
- example: NA
- type: int

#### MGMT_GW

Default Gateway For Management VRF On The Switch

- default: 
- example: NA
- type: str

#### MGMT_PREFIX

No description available

- default: 24
- example: NA
- type: int

#### MGMT_V6PREFIX

No description available

- default: 64
- example: NA
- type: int

#### MPLS_HANDOFF

No description available

- default: 0
- example: NA
- type: bool

#### MPLS_LB_ID

Used for VXLAN to MPLS SR/LDP Handoff 

- default: 101
- example: NA
- type: int

#### MPLS_LOOPBACK_IP_RANGE

Used for VXLAN to MPLS SR/LDP Handoff

- default: 10.101.0.0/25
- example: NA
- type: str

#### MST_INSTANCE_RANGE

MST instance range, Example: 0-3,5,7-9, Default is 0

- default: 0
- example: NA
- type: str

#### MULTICAST_GROUP_SUBNET

Multicast pool prefix between 8 to 30. A multicast group IP from this pool is used for BUM traffic for each overlay network.

- default: 239.1.1.0/25
- example: NA
- type: str

#### NETFLOW_EXPORTER_LIST

One or Multiple Netflow Exporters

- default: 
- example: NA
- type: list

#### NETFLOW_MONITOR_LIST

One or Multiple Netflow Monitors

- default: 
- example: NA
- type: list

#### NETFLOW_RECORD_LIST

One or Multiple Netflow Records

- default: 
- example: NA
- type: list

#### NETWORK_VLAN_RANGE

Per Switch Overlay Network VLAN Range 

- default: 2300-2999
- example: NA
- type: str

#### NTP_SERVER_IP_LIST

Comma separated list of IP Addresses(v4/v6)

- default: 
- example: NA
- type: str

#### NTP_SERVER_VRF

One VRF for all NTP servers or a comma separated list of VRFs, one per NTP server

- default: 
- example: NA
- type: str

#### NVE_LB_ID

No description available

- default: 1
- example: NA
- type: int

#### NXAPI_HTTPS_PORT

No description available

- default: 443
- example: NA
- type: int

#### NXAPI_HTTP_PORT

No description available

- default: 80
- example: NA
- type: int

#### OBJECT_TRACKING_NUMBER_RANGE

Per switch tracked object ID Range 

- default: 100-299
- example: NA
- type: str

#### OSPF_AREA_ID

OSPF Area Id in IP address format

- default: 0.0.0.0
- example: NA
- type: str

#### OSPF_AUTH_ENABLE

No description available

- default: 0
- example: NA
- type: bool

#### OSPF_AUTH_KEY

3DES Encrypted

- default: 
- example: NA
- type: str

#### OSPF_AUTH_KEY_ID

No description available

- default: 127
- example: NA
- type: int

#### OVERLAY_MODE

VRF/Network configuration using config-profile or CLI

- default: cli
- example: NA
- type: str

#### PER_VRF_LOOPBACK_AUTO_PROVISION

Auto provision a loopback on a VTEP on VRF attachment

- default: 0
- example: NA
- type: bool

#### PER_VRF_LOOPBACK_IP_RANGE

Prefix pool to assign IP addresses to loopbacks on VTEPs on a per VRF basis

- default: 10.5.0.0/22
- example: NA
- type: str

#### PHANTOM_RP_LB_ID1

Used for Bidir-PIM Phantom RP 

- default: 2
- example: NA
- type: int

#### PHANTOM_RP_LB_ID2

Used for Fallback Bidir-PIM Phantom RP 

- default: 3
- example: NA
- type: int

#### PHANTOM_RP_LB_ID3

Used for second Fallback Bidir-PIM Phantom RP 

- default: 4
- example: NA
- type: int

#### PHANTOM_RP_LB_ID4

Used for third Fallback Bidir-PIM Phantom RP 

- default: 5
- example: NA
- type: int

#### PIM_HELLO_AUTH_ENABLE

Valid for IPv4 Underlay only

- default: 0
- example: NA
- type: bool

#### PIM_HELLO_AUTH_KEY

3DES Encrypted

- default: 
- example: NA
- type: str

#### PM_ENABLE

No description available

- default: 0
- example: NA
- type: bool

#### POWER_REDUNDANCY_MODE

Default Power Supply Mode For The Fabric

- default: ps-redundant
- example: NA
- type: str

#### PTP_DOMAIN_ID

Multiple Independent PTP Clocking Subdomains on a Single Network 

- default: 0
- example: NA
- type: int

#### PTP_LB_ID

No description available

- default: 0
- example: NA
- type: int

#### REPLICATION_MODE

Replication Mode for BUM Traffic

- default: Multicast
- example: NA
- type: str

#### ROUTER_ID_RANGE

No description available

- default: 10.2.0.0/23
- example: NA
- type: str

#### ROUTE_MAP_SEQUENCE_NUMBER_RANGE

No description available

- default: 1-65534
- example: NA
- type: str

#### RP_COUNT

Number of spines acting as Rendezvous-Point (RP)

- default: 2
- example: NA
- type: int

#### RP_LB_ID

No description available

- default: 254
- example: NA
- type: int

#### RP_MODE

Multicast RP Mode

- default: asm
- example: NA
- type: str

#### RR_COUNT

Number of spines acting as Route-Reflectors

- default: 2
- example: NA
- type: int

#### SEED_SWITCH_CORE_INTERFACES

Core-facing Interface list on Seed Switch (e.g. e1/1-30,e1/32)

- default: 
- example: NA
- type: str

#### SERVICE_NETWORK_VLAN_RANGE

Per Switch Overlay Service Network VLAN Range 

- default: 3000-3199
- example: NA
- type: str

#### SITE_ID

For EVPN Multi-Site Support . Defaults to Fabric ASN

- default: 
- example: NA
- type: str

#### SLA_ID_RANGE

Per switch SLA ID Range 

- default: 10000-19999
- example: NA
- type: str

#### SNMP_SERVER_HOST_TRAP

Configure NDFC as a receiver for SNMP traps

- default: 1
- example: NA
- type: bool

#### SPINE_SWITCH_CORE_INTERFACES

Core-facing Interface list on all Spines (e.g. e1/1-30,e1/32)

- default: 
- example: NA
- type: str

#### STATIC_UNDERLAY_IP_ALLOC

Checking this will disable Dynamic Underlay IP Address Allocations

- default: 0
- example: NA
- type: bool

#### STP_BRIDGE_PRIORITY

Bridge priority for the spanning tree in increments of 4096

- default: 0
- example: NA
- type: str

#### STP_ROOT_OPTION

Which protocol to use for configuring root bridge? rpvst+: Rapid Per-VLAN Spanning Tree, mst: Multiple Spanning Tree, unmanaged (default): STP Root not managed by NDFC

- default: unmanaged
- example: NA
- type: str

#### STP_VLAN_RANGE

Vlan range, Example: 1,3-5,7,9-11, Default is 1-3967

- default: 1-3967
- example: NA
- type: str

#### STRICT_CC_MODE

Enable bi-directional compliance checks to flag additional configs in the running config that are not in the intent/expected config

- default: 0
- example: NA
- type: bool

#### SUBINTERFACE_RANGE

Per Border Dot1q Range For VRF Lite Connectivity 

- default: 2-511
- example: NA
- type: str

#### SUBNET_RANGE

Address range to assign Numbered and Peer Link SVI IPs

- default: 10.4.0.0/16
- example: NA
- type: str

#### SUBNET_TARGET_MASK

Mask for Underlay Subnet IP Range

- default: 30
- example: NA
- type: int

#### SYSLOG_SERVER_IP_LIST

Comma separated list of IP Addresses(v4/v6)

- default: 
- example: NA
- type: str

#### SYSLOG_SERVER_VRF

One VRF for all Syslog servers or a comma separated list of VRFs, one per Syslog server

- default: 
- example: NA
- type: str

#### SYSLOG_SEV

Comma separated list of Syslog severity values, one per Syslog server 

- default: 
- example: NA
- type: str

#### TCAM_ALLOCATION

TCAM commands are automatically generated for VxLAN and vPC Fabric Peering when Enabled

- default: 1
- example: NA
- type: bool

#### UNDERLAY_IS_V6

If not enabled, IPv4 underlay is used

- default: 0
- example: NA
- type: bool

#### UNNUM_BOOTSTRAP_LB_ID

No description available

- default: 253
- example: NA
- type: int

#### UNNUM_DHCP_END

Must be a subset of IGP/BGP Loopback Prefix Pool

- default: 
- example: NA
- type: str

#### UNNUM_DHCP_START

Must be a subset of IGP/BGP Loopback Prefix Pool

- default: 
- example: NA
- type: str

#### USE_LINK_LOCAL

If not enabled, Spine-Leaf interfaces will use global IPv6 addresses

- default: 1
- example: NA
- type: bool

#### V6_SUBNET_RANGE

IPv6 Address range to assign Numbered and Peer Link SVI IPs

- default: fd00::a04:0/112
- example: NA
- type: str

#### V6_SUBNET_TARGET_MASK

Mask for Underlay Subnet IPv6 Range

- default: 126
- example: NA
- type: int

#### VPC_AUTO_RECOVERY_TIME

No description available

- default: 360
- example: NA
- type: int

#### VPC_DELAY_RESTORE

No description available

- default: 150
- example: NA
- type: int

#### VPC_DOMAIN_ID_RANGE

vPC Domain id range to use for new pairings

- default: 1-1000
- example: NA
- type: str

#### VPC_ENABLE_IPv6_ND_SYNC

Enable IPv6 ND synchronization between vPC peers

- default: 1
- example: NA
- type: bool

#### VPC_PEER_KEEP_ALIVE_OPTION

Use vPC Peer Keep Alive with Loopback or Management

- default: management
- example: NA
- type: str

#### VPC_PEER_LINK_PO

No description available

- default: 500
- example: NA
- type: str

#### VPC_PEER_LINK_VLAN

VLAN range for vPC Peer Link SVI 

- default: 3600
- example: NA
- type: str

#### VRF_LITE_AUTOCONFIG

VRF Lite Inter-Fabric Connection Deployment Options. If Back2Back&ToExternal is selected, VRF Lite IFCs are auto created between border devices of two Easy Fabrics, and between border devices in Easy Fabric and edge routers in External Fabric. The IP address is taken from the VRF Lite Subnet IP Range pool.

- default: Manual
- example: NA
- type: str

#### VRF_VLAN_RANGE

Per Switch Overlay VRF VLAN Range 

- default: 2000-2299
- example: NA
- type: str

#### default_network

Default Overlay Network Template For Leafs

- default: Default_Network_Universal
- example: NA
- type: str

#### default_pvlan_sec_network

Default PVLAN Secondary Network Template

- default: Pvlan_Secondary_Network
- example: NA
- type: str

#### default_vrf

Default Overlay VRF Template For Leafs

- default: Default_VRF_Universal
- example: NA
- type: str

#### enableRealTimeBackup

Backup hourly only if there is any config deployment since last backup

- default: 
- example: NA
- type: bool

#### enableScheduledBackup

Backup at the specified time

- default: 
- example: NA
- type: bool

#### network_extension_template

Default Overlay Network Template For Borders

- default: Default_Network_Extension_Universal
- example: NA
- type: str

#### scheduledTime

Time (UTC) in 24hr format. (00:00 to 23:59)

- default: 
- example: NA
- type: str

#### vrf_extension_template

Default Overlay VRF Template For Borders

- default: Default_VRF_Extension_Universal
- example: NA
- type: str

