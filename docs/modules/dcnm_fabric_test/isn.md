#### AAA_REMOTE_IP_ENABLED

Enable only, when IP Authorization is enabled in the AAA Server

- default: False
- example: NA
- type: bool

#### AAA_SERVER_CONF

AAA Configurations

- default: 
- example: NA
- type: str

#### BGP_AS

1-4294967295 | 1-65535.0-65535 It is a good practice to have a unique ASN for each Fabric.

- default: 
- example: NA
- type: str

#### BOOTSTRAP_CONF

Additional CLIs required during device bootup/login e.g. AAA/Radius

- default: 
- example: NA
- type: str

#### BOOTSTRAP_CONF_XE

Additional CLIs required during device bootup/login e.g. AAA/Radius

- default: 
- example: NA
- type: str

#### BOOTSTRAP_ENABLE

Automatic IP Assignment For POAP

- default: False
- example: NA
- type: bool

#### BOOTSTRAP_MULTISUBNET

lines with # prefix are ignored here

- default: #Scope_Start_IP, Scope_End_IP, Scope_Default_Gateway, Scope_Subnet_Prefix
- example: NA
- type: str

#### CDP_ENABLE

Enable CDP on management interface

- default: False
- example: NA
- type: bool

#### DEPLOY

Save and deploy the fabric configuration.

- default: False
- example: NA
- type: bool

#### DHCP_ENABLE

Automatic IP Assignment For POAP From Local DHCP Server

- default: False
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

#### DOMAIN_NAME

Domain name for DHCP server PnP block

- default: 
- example: NA
- type: str

#### ENABLE_AAA

Include AAA configs from Advanced tab during device bootup

- default: False
- example: NA
- type: bool

#### ENABLE_NETFLOW

Enable Netflow on VTEPs

- default: False
- example: NA
- type: bool

#### ENABLE_NXAPI

Enable HTTPS NX-API

- default: False
- example: NA
- type: bool

#### ENABLE_NXAPI_HTTP

No description available

- default: False
- example: NA
- type: bool

#### ENABLE_RT_INTF_STATS

Valid for NX-OS only

- default: False
- example: NA
- type: bool

#### FABRIC_FREEFORM

Additional supported CLIs for all same OS (e.g. all NxOS or IOS-XE, etc) switches

- default: 
- example: NA
- type: str

#### FABRIC_NAME

The name of the fabric.

- default: None
- example: NA
- type: str

#### FABRIC_TYPE

The type of fabric.

- default: None
- example: NA
- type: str

#### FEATURE_PTP

No description available

- default: False
- example: NA
- type: bool

#### INBAND_ENABLE

Enable POAP over Inband Interface (Pre-req: Inband Mgmt Knob should be Enabled)

- default: False
- example: NA
- type: bool

#### INBAND_MGMT

Import switches with inband connectivity

- default: False
- example: NA
- type: bool

#### INTF_STAT_LOAD_INTERVAL

Time in seconds 

- default: 10
- example: NA
- type: int

#### IS_READ_ONLY

If enabled, fabric is only monitored. No configuration will be deployed

- default: True
- example: NA
- type: bool

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

- default: False
- example: NA
- type: bool

#### MPLS_LB_ID

No description available

- default: 101
- example: NA
- type: int

#### MPLS_LOOPBACK_IP_RANGE

MPLS Loopback IP Address Range

- default: 10.102.0.0/25
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

#### NETFLOW_SAMPLER_LIST

One or multiple netflow samplers. Applicable to N7K only

- default: 
- example: NA
- type: list

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

#### PM_ENABLE

No description available

- default: False
- example: NA
- type: bool

#### PNP_ENABLE

Enable Plug n Play (Automatic IP Assignment) for Cat9K switches

- default: False
- example: NA
- type: bool

#### POWER_REDUNDANCY_MODE

Default Power Supply Mode For Bootstrapped NX-OS Switches

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

#### SNMP_SERVER_HOST_TRAP

Configure NDFC as a receiver for SNMP traps

- default: True
- example: NA
- type: bool

#### SUBINTERFACE_RANGE

Per Border Dot1q Range For VRF Lite Connectivity 

- default: 2-511
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

#### scheduledTime

Time (UTC) in 24hr format. (00:00 to 23:59)

- default: 
- example: NA
- type: str

