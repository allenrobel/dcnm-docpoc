#### ANYCAST_GW_MAC

Shared MAC address for all leaves

- default: 2020.0000.00aa
- example: NA
- type: str

#### BGP_RP_ASN

1-4294967295 | 1-65535.0-65535, e.g. 65000, 65001

- default: 
- example: NA
- type: str

#### BGW_ROUTING_TAG

Routing tag associated with IP address of loopback and DCI interfaces

- default: 54321
- example: NA
- type: str

#### BORDER_GWY_CONNECTIONS

Manual, Auto Overlay EVPN Peering to Route Servers, Auto Overlay EVPN Direct Peering to Border Gateways

- default: Manual
- example: NA
- type: str

#### CLOUDSEC_ALGORITHM

AES_128_CMAC or AES_256_CMAC

- default: AES_128_CMAC
- example: NA
- type: str

#### CLOUDSEC_AUTOCONFIG

Auto Config CloudSec on Border Gateways

- default: 0
- example: NA
- type: bool

#### CLOUDSEC_ENFORCEMENT

If set to strict, data across site must be encrypted.

- default: 
- example: NA
- type: str

#### CLOUDSEC_KEY_STRING

Cisco Type 7 Encrypted Octet String

- default: 
- example: NA
- type: str

#### CLOUDSEC_REPORT_TIMER

CloudSec Operational Status periodic report timer in minutes

- default: 5
- example: NA
- type: int

#### DCI_SUBNET_RANGE

Address range to assign P2P DCI Links

- default: 10.10.1.0/24
- example: NA
- type: str

#### DCI_SUBNET_TARGET_MASK

Target Mask for Subnet Range 

- default: 30
- example: NA
- type: int

#### DELAY_RESTORE

Multi-Site underlay and overlay control plane convergence time  in seconds

- default: 300
- example: NA
- type: int

#### DEPLOY

Save and deploy the fabric configuration.

- default: False
- example: NA
- type: bool

#### ENABLE_BGP_BFD

For auto-created Multi-Site Underlay IFCs

- default: 0
- example: NA
- type: bool

#### ENABLE_BGP_LOG_NEIGHBOR_CHANGE

For auto-created Multi-Site Underlay IFCs

- default: 0
- example: NA
- type: bool

#### ENABLE_BGP_SEND_COMM

For auto-created Multi-Site Underlay IFCs

- default: 0
- example: NA
- type: bool

#### ENABLE_PVLAN

Enable PVLAN on MSD and its child fabrics

- default: 0
- example: NA
- type: bool

#### ENABLE_RS_REDIST_DIRECT

For auto-created Multi-Site overlay IFCs in Route Servers. Applicable only when Multi-Site Overlay IFC Deployment Method is Centralized_To_Route_Server.

- default: 0
- example: NA
- type: bool

#### FABRIC_NAME

Please provide the fabric name to create it (Max Size 64)

- default: 
- example: NA
- type: str

#### FABRIC_TYPE

The type of fabric.

- default: None
- example: NA
- type: str

#### L2_SEGMENT_ID_RANGE

Overlay Network Identifier Range 

- default: 30000-49000
- example: NA
- type: str

#### L3_PARTITION_ID_RANGE

Overlay VRF Identifier Range 

- default: 50000-59000
- example: NA
- type: str

#### LOOPBACK100_IP_RANGE

Typically Loopback100 IP Address Range

- default: 10.10.0.0/24
- example: NA
- type: str

#### MS_IFC_BGP_AUTH_KEY_TYPE

BGP Key Encryption Type: 3 - 3DES, 7 - Cisco

- default: 3
- example: NA
- type: str

#### MS_IFC_BGP_PASSWORD

Encrypted eBGP Password Hex String

- default: 
- example: NA
- type: str

#### MS_IFC_BGP_PASSWORD_ENABLE

eBGP password for Multi-Site underlay/overlay IFCs

- default: 0
- example: NA
- type: bool

#### MS_LOOPBACK_ID

No description available

- default: 100
- example: NA
- type: int

#### MS_UNDERLAY_AUTOCONFIG

No description available

- default: 0
- example: NA
- type: bool

#### RP_SERVER_IP

Multi-Site Route-Server peer list (typically loopback IP address on Route-Server for Multi-Site EVPN peering with BGWs), e.g. 128.89.0.1, 128.89.0.2

- default: 
- example: NA
- type: str

#### RS_ROUTING_TAG

Routing tag associated with Route Server IP for redistribute direct. This is the IP used in eBGP EVPN peering.

- default: 54321
- example: NA
- type: str

#### TOR_AUTO_DEPLOY

Enables Overlay VLANs on uplink between ToRs and Leafs

- default: 0
- example: NA
- type: bool

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

#### enableScheduledBackup

Backup at the specified time. Note: Fabric Backup/Restore functionality is being deprecated for MSD fabrics. Recommendation is to use NDFC Backup & Restore

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

