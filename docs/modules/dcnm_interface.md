# dcnm_interface

???+ "Details"

    - author
        - Mallik Mudigonda(@mmudigon)
    - description
        - DCNM Ansible Module for the following interface service operations 
        - Create, Delete, Modify PortChannel, VPC, Loopback and Sub-Interfaces 
        - Modify Ethernet Interfaces
    - short_description
        - DCNM Ansible Module for managing interfaces.
    - version_added
        - 0.9.0


## options

???+ "Details"


### check_deploy

???+ "Details"

    - default
        - False
    - description
        - Deploy operations may take considerable time in certain cases based on the configuration included in the playbook. A success response from DCNM server does not guarantee the completion of deploy operation. This flag if set indicates that the module should verify if the configured state is in sync with what is requested in playbook. If not set the module will return without verifying the state.
    - required
        - False
    - type
        - bool

### config

???+ "Details"

    - default
        - []
    - description
        - A dictionary of interface operations
    - elements
        - dict

#### deploy

???+ "Details"

    - default
        - True
    - description
        - Flag indicating if the configuration must be pushed to the switch. If not included it is considered true by default
    - type
        - bool

#### name

???+ "Details"

    - description
        - Name of the interface. Example, po55, eth2/1, lo100, vpc25, eth1/1.1.
    - required
        - True
    - type
        - str

#### profile_aa_fex

???+ "Details"

    - description
        - Though the key shown here is 'profile_aa_fex' the actual key to be used in playbook is 'profile'. The key 'profile_aa_fex' is used here to logically segregate the interface objects applicable for this profile 
        - Object profile which must be included for active-active FEX inetrface configurations.

##### admin_state

???+ "Details"

    - default
        - True
    - description
        - Administrative state of the interface
    - type
        - bool

##### description

???+ "Details"

    - default
        - 
    - description
        - Description of the FEX interface
    - type
        - str

##### enable_netflow

???+ "Details"

    - default
        - False
    - description
        - Flag to enable netflow.
    - type
        - bool

##### mode

???+ "Details"

    - choices
        - port_channel_aa
    - description
        - Interface mode
    - required
        - True
    - type
        - str

##### mtu

???+ "Details"

    - choices
        - default
        - jumbo
    - default
        - jumbo
    - description
        - Interface MTU
    - type
        - str

##### netflow_monitor

???+ "Details"

    - default
        - 
    - description
        - Name of netflow monitor. This parameter is required if "enable_netflow" is True.
    - type
        - str

##### peer1_cmds

???+ "Details"

    - default
        - []
    - description
        - Commands to be included in the configuration under this interface of first peer
    - elements
        - str
    - type
        - list

##### peer1_members

???+ "Details"

    - description
        - Member interfaces that are part of this port channel on first peer
    - elements
        - str
    - required
        - True
    - type
        - list

##### peer1_po_description

???+ "Details"

    - default
        - 
    - description
        - Description of the port-channel interface of first peer
    - type
        - str

##### peer2_cmds

???+ "Details"

    - default
        - []
    - description
        - Commands to be included in the configuration under this interface of second peer
    - elements
        - str
    - type
        - list

##### peer2_members

???+ "Details"

    - description
        - Member interfaces that are part of this port channel on second peer
    - elements
        - str
    - required
        - True
    - type
        - list

##### peer2_po_description

???+ "Details"

    - default
        - 
    - description
        - Description of the port-channel interface of second peer
    - type
        - str

#### profile_eth

???+ "Details"

    - description
        - Though the key shown here is 'profile_eth' the actual key to be used in playbook is 'profile'. The key 'profile_eth' is used here to logically segregate the interface objects applicable for this profile 
        - Object profile which must be included for ethernet interface configurations.

##### access_vlan

???+ "Details"

    - default
        - 
    - description
        - Vlan for the interface. This option is applicable only for interfaces whose 'mode' is 'access'
    - type
        - str

##### admin_state

???+ "Details"

    - default
        - True
    - description
        - Administrative state of the interface
    - type
        - bool

##### allowed_vlans

???+ "Details"

    - choices
        - none
        - all
        - vlan-range(e.g., 1-2, 3-40)
    - default
        - none
    - description
        - Vlans that are allowed on this interface. This option is applicable only for interfaces whose 'mode' is 'trunk'
    - type
        - str

##### bpdu_guard

???+ "Details"

    - choices
        - true
        - false
        - no
    - default
        - true
    - description
        - Spanning-tree bpduguard
    - type
        - str

##### cmds

???+ "Details"

    - default
        - []
    - description
        - Commands to be included in the configuration under this interface
    - elements
        - str
    - type
        - list

##### description

???+ "Details"

    - default
        - 
    - description
        - Description of the interface
    - type
        - str

##### int_vrf

???+ "Details"

    - default
        - default
    - description
        - Interface VRF name. This object is applicable only if the 'mode' is 'routed'
    - type
        - str

##### ipv4_addr

???+ "Details"

    - default
        - 
    - description
        - IPV4 address of the interface. This object is applicable only if the 'mode' is 'routed' or 'epl_routed'
    - type
        - str

##### ipv4_mask_len

???+ "Details"

    - default
        - 8
    - description
        - IPV4 address mask length. This object is applicable only if the 'mode' is 'routed' or 'epl_routed' 
        - Minimum Value (1), Maximum Value (31)
    - type
        - int

##### ipv6_addr

???+ "Details"

    - default
        - 
    - description
        - IPV6 address of the interface. This object is applicable only if the 'mode' is 'epl_routed'
    - type
        - str

##### ipv6_mask_len

???+ "Details"

    - default
        - 8
    - description
        - IPV6 address mask length. This object is applicable only if the 'mode' is 'epl_routed' 
        - Minimum Value (1), Maximum Value (31)
    - type
        - int

##### mode

???+ "Details"

    - choices
        - trunk
        - access
        - routed
        - monitor
        - epl_routed
    - description
        - Interface mode
    - required
        - True
    - type
        - str

##### mtu

???+ "Details"

    - description
        - Interface MTU. 
        - Can be specified either "default" or "jumbo" for access and trunk interface types. If not specified, it defaults to "jumbo" 
        - Can be specified with any value within 576 and 9216 for routed interface types. If not specified, it defaults to 9216
    - type
        - str

##### port_type_fast

???+ "Details"

    - choices
        - True
        - False
    - default
        - True
    - description
        - Spanning-tree edge port behavior
    - type
        - bool

##### route_tag

???+ "Details"

    - default
        - 
    - description
        - Route tag associated with the interface IP. This object is applicable only if the 'mode' is 'routed' or 'epl_routed'
    - type
        - str

##### speed

???+ "Details"

    - default
        - Auto
    - description
        - Speed of the interface.
    - type
        - str

#### profile_lo

???+ "Details"

    - description
        - Though the key shown here is 'profile_lo' the actual key to be used in playbook is 'profile'. The key 'profile_lo' is used here to logically segregate the interface objects applicable for this profile 
        - Object profile which must be included for loopback interface configurations.

##### admin_state

???+ "Details"

    - default
        - True
    - description
        - Administrative state of the interface
    - type
        - bool

##### cmds

???+ "Details"

    - default
        - []
    - description
        - Commands to be included in the configuration under this interface
    - elements
        - str
    - type
        - list

##### description

???+ "Details"

    - default
        - 
    - description
        - Description of the interface
    - type
        - str

##### int_vrf

???+ "Details"

    - default
        - default
    - description
        - Interface VRF name.
    - type
        - str

##### ipv4_addr

???+ "Details"

    - default
        - 
    - description
        - IPv4 address of the interface.
    - type
        - str

##### ipv6_addr

???+ "Details"

    - default
        - 
    - description
        - IPv6 address of the interface.
    - type
        - str

##### mode

???+ "Details"

    - choices
        - lo
        - fabric
        - mpls
    - description
        - There are several modes for loopback interfaces. 
        - Mode 'lo' is used to create, modify and delete non fabric loopback interfaces using policy 'int_loopback'. 
        - Mode 'fabric' is used to modify loopbacks created when the fabric is first created using policy 'int_fabric_loopback_11_1' 
        - Mode 'mpls' is used to modify loopbacks created when the fabric is first created using policy 'int_mpls_loopback' 
        - Mode 'fabric' and 'mpls' interfaces can be modified but not created or deleted.
    - required
        - True
    - type
        - str

##### route_tag

???+ "Details"

    - default
        - 
    - description
        - Route tag associated with the interface IP.
    - type
        - str

##### secondary_ipv4_addr

???+ "Details"

    - default
        - 
    - description
        - Secondary IP address of the nve interface loopback
    - type
        - str

#### profile_pc

???+ "Details"

    - description
        - Though the key shown here is 'profile_pc' the actual key to be used in playbook is 'profile'. The key 'profile_pc' is used here to logically segregate the interface objects applicable for this profile 
        - Object profile which must be included for port channel interface configurations.

##### access_vlan

???+ "Details"

    - default
        - 
    - description
        - Vlan for the interface. This option is applicable only for interfaces whose 'mode' is 'access'
    - type
        - str

##### admin_state

???+ "Details"

    - default
        - True
    - description
        - Administrative state of the interface
    - type
        - bool

##### cmds

???+ "Details"

    - default
        - []
    - description
        - Commands to be included in the configuration under this interface
    - elements
        - str
    - type
        - list

##### description

???+ "Details"

    - default
        - 
    - description
        - Description of the interface
    - type
        - str

##### int_vrf

???+ "Details"

    - default
        - default
    - description
        - Interface VRF name. This object is applicable only if the 'mode' is 'l3'
    - type
        - str

##### ipv4_addr

???+ "Details"

    - default
        - 
    - description
        - IPV4 address of the interface. This object is applicable only if the 'mode' is 'l3'
    - type
        - str

##### ipv4_mask_len

???+ "Details"

    - default
        - 8
    - description
        - IPV4 address mask length. This object is applicable only if the 'mode' is 'l3' 
        - Minimum Value (1), Maximum Value (31)
    - type
        - int

##### members

???+ "Details"

    - description
        - Member interfaces that are part of this port channel
    - elements
        - str
    - required
        - True
    - type
        - list

##### mode

???+ "Details"

    - choices
        - trunk
        - access
        - l3
        - monitor
    - description
        - Interface mode
    - required
        - True
    - type
        - str

##### route_tag

???+ "Details"

    - default
        - 
    - description
        - Route tag associated with the interface IP. This object is applicable only if the 'mode' is 'l3'
    - type
        - str

#### profile_st_fex

???+ "Details"

    - description
        - Though the key shown here is 'profile_st_fex' the actual key to be used in playbook is 'profile'. The key 'profile_st_fex' is used here to logically segregate the interface objects applicable for this profile 
        - Object profile which must be included for straigth-through FEX interface configurations.

##### admin_state

???+ "Details"

    - default
        - True
    - description
        - Administrative state of the interface
    - type
        - bool

##### cmds

???+ "Details"

    - default
        - []
    - description
        - Commands to be included in the configuration under this interface
    - elements
        - str
    - type
        - list

##### description

???+ "Details"

    - default
        - 
    - description
        - Description of the FEX interface
    - type
        - str

##### enable_netflow

???+ "Details"

    - default
        - False
    - description
        - Flag to enable netflow.
    - type
        - bool

##### members

???+ "Details"

    - description
        - Member interfaces that are part of this FEX
    - elements
        - str
    - required
        - True
    - type
        - list

##### mode

???+ "Details"

    - choices
        - port_channel_st
    - description
        - Interface mode
    - required
        - True
    - type
        - str

##### mtu

???+ "Details"

    - choices
        - default
        - jumbo
    - default
        - jumbo
    - description
        - Interface MTU.
    - type
        - str

##### netflow_monitor

???+ "Details"

    - default
        - 
    - description
        - Name of netflow monitor. This parameter is required if "enable_netflow" is True.
    - type
        - str

##### po_description

???+ "Details"

    - default
        - 
    - description
        - Description of the port-channel which is part of the FEX interface
    - type
        - str

#### profile_subint

???+ "Details"

    - description
        - Though the key shown here is 'profile_subint' the actual key to be used in playbook is 'profile'. The key 'profile_subint' is used here to logically segregate the interface objects applicable for this profile 
        - Object profile which must be included for sub-interface configurations.

##### admin_state

???+ "Details"

    - default
        - True
    - description
        - Administrative state of the interface
    - type
        - bool

##### cmds

???+ "Details"

    - default
        - []
    - description
        - Commands to be included in the configuration under this interface
    - elements
        - str
    - type
        - list

##### description

???+ "Details"

    - default
        - 
    - description
        - Description of the interface
    - type
        - str

##### int_vrf

???+ "Details"

    - default
        - default
    - description
        - Interface VRF name.
    - type
        - str

##### ipv4_addr

???+ "Details"

    - default
        - 
    - description
        - IPV4 address of the interface.
    - type
        - str

##### ipv4_mask_len

???+ "Details"

    - default
        - 8
    - description
        - IPV4 address mask length. 
        - Minimum Value (8), Maximum Value (31)
    - type
        - int

##### ipv6_addr

???+ "Details"

    - default
        - 
    - description
        - IPV6 address of the interface.
    - type
        - str

##### ipv6_mask_len

???+ "Details"

    - default
        - 8
    - description
        - IPV6 address mask length. 
        - Minimum Value (1), Maximum Value (31)
    - type
        - int

##### mode

???+ "Details"

    - choices
        - subint
    - description
        - Interface mode
    - required
        - True
    - type
        - str

##### mtu

???+ "Details"

    - default
        - 9216
    - description
        - Interface MTU 
        - Minimum Value (567), Maximum Value (9216)
    - type
        - int

##### vlan

???+ "Details"

    - default
        - 0
    - description
        - DOT1Q vlan id for this interface 
        - Minimum Value (2), Maximum Value (3967)
    - type
        - int

#### profile_svi

???+ "Details"

    - description
        - Though the key shown here is 'profile_svi' the actual key to be used in playbook is 'profile'. The key 'profile_svi' is used here to logically segregate the interface objects applicable for this profile 
        - Object profile which must be included for SVI interface configurations.

##### admin_state

???+ "Details"

    - description
        - Administrative state of the interface.
    - required
        - True
    - type
        - bool

##### adv_subnet_in_underlay

???+ "Details"

    - default
        - False
    - description
        - Flag to enable/disable advertisements of subnets into underlay.
    - type
        - bool

##### cmds

???+ "Details"

    - default
        - []
    - description
        - Commands to be included in the configuration under this interface.
    - elements
        - str
    - type
        - list

##### description

???+ "Details"

    - default
        - 
    - description
        - Description of the interface.
    - type
        - str

##### dhcp_server_addr1

???+ "Details"

    - default
        - 
    - description
        - DHCP relay server address.
    - type
        - str

##### dhcp_server_addr2

???+ "Details"

    - default
        - 
    - description
        - DHCP relay server address.
    - type
        - str

##### dhcp_server_addr3

???+ "Details"

    - default
        - 
    - description
        - DHCP relay server address.
    - type
        - str

##### disable_ip_redirects

???+ "Details"

    - default
        - False
    - description
        - Flag to enable/disable IP redirects.
    - type
        - bool

##### enable_hsrp

???+ "Details"

    - default
        - False
    - description
        - Flag to enable/disable HSRP on the interface.
    - type
        - bool

##### enable_netflow

???+ "Details"

    - default
        - False
    - description
        - Flag to enable netflow.
    - type
        - bool

##### hsrp_group

???+ "Details"

    - default
        - 
    - description
        - HSRP group. This parameter is required if "enable_hsrp" is True.
    - type
        - str

##### hsrp_priority

???+ "Details"

    - default
        - 
    - description
        - HSRP priority.
    - type
        - str

##### hsrp_version

???+ "Details"

    - choices
        - 1
        - 2
    - default
        - 1
    - description
        - HSRP protocol version.
    - type
        - int

##### hsrp_vip

???+ "Details"

    - default
        - 
    - description
        - Virtual IP address for HSRP. This parameter is required if "enable_hsrp" is True.
    - type
        - str

##### hsrp_vmac

???+ "Details"

    - default
        - 
    - description
        - HSRP virtual MAC.
    - type
        - str

##### int_vrf

???+ "Details"

    - default
        - default
    - description
        - Interface VRF name.
    - type
        - str

##### ipv4_addr

???+ "Details"

    - default
        - 
    - description
        - IPV4 address of the interface.
    - type
        - str

##### ipv4_mask_len

???+ "Details"

    - description
        - IPV4 address mask length. This parameter is required if 'ipv4_addr' is included. 
        - Minimum Value (1), Maximum Value (31)
    - type
        - int

##### mode

???+ "Details"

    - choices
        - vlan
    - description
        - Interface mode.
    - required
        - True
    - type
        - str

##### mtu

???+ "Details"

    - default
        - 9216
    - description
        - Interface MTU.
    - type
        - int

##### netflow_monitor

???+ "Details"

    - default
        - 
    - description
        - Name of netflow monitor. This parameter is required if "enable_netflow" is True.
    - type
        - str

##### preempt

???+ "Details"

    - default
        - False
    - description
        - Flag to enable/disable overthrow of low priority active routers. This parameter is valid only if "enable_hsrp" is True.
    - type
        - bool

##### route_tag

???+ "Details"

    - default
        - 
    - description
        - Route tag associated with the interface IP.
    - type
        - str

##### vrf_dhcp1

???+ "Details"

    - default
        - 
    - description
        - VRF to reach DHCP server. This parameter is required if "dhcp_server_addr1" is included.
    - type
        - str

##### vrf_dhcp2

???+ "Details"

    - default
        - 
    - description
        - VRF to reach DHCP server. This parameter is required if "dhcp_server_addr2" is included.
    - type
        - str

##### vrf_dhcp3

???+ "Details"

    - default
        - 
    - description
        - VRF to reach DHCP server. This parameter is required if "dhcp_server_addr3" is included.
    - type
        - str

#### profile_vpc

???+ "Details"

    - description
        - Though the key shown here is 'profile_vpc' the actual key to be used in playbook is 'profile'. The key 'profile_vpc' is used here to logically segregate the interface objects applicable for this profile 
        - Object profile which must be included for virtual port channel inetrface configurations.

##### admin_state

???+ "Details"

    - default
        - True
    - description
        - Administrative state of the interface
    - type
        - bool

##### bpdu_guard

???+ "Details"

    - choices
        - true
        - false
        - no
    - default
        - true
    - description
        - Spanning-tree bpduguard
    - type
        - str

##### mode

???+ "Details"

    - choices
        - trunk
        - access
    - description
        - Interface mode
    - required
        - True
    - type
        - str

##### mtu

???+ "Details"

    - choices
        - default
        - jumbo
    - default
        - jumbo
    - description
        - Interface MTU
    - type
        - str

##### pc_mode

???+ "Details"

    - choices
        - active
        - passive
        - on
    - default
        - active
    - description
        - Port channel mode
    - type
        - str

##### peer1_access_vlan

???+ "Details"

    - default
        - 
    - description
        - Vlan for the interface of first peer. This option is applicable only for interfaces whose 'mode' is 'access'
    - type
        - str

##### peer1_allowed_vlans

???+ "Details"

    - choices
        - none
        - all
        - vlan-range(e.g., 1-2, 3-40)
    - default
        - none
    - description
        - Vlans that are allowed on this interface of first peer. This option is applicable only for interfaces whose 'mode' is 'trunk'
    - type
        - str

##### peer1_cmds

???+ "Details"

    - default
        - []
    - description
        - Commands to be included in the configuration under this interface of first peer
    - elements
        - str
    - type
        - list

##### peer1_description

???+ "Details"

    - default
        - 
    - description
        - Description of the interface of first peer
    - type
        - str

##### peer1_members

???+ "Details"

    - description
        - Member interfaces that are part of this port channel on first peer
    - elements
        - str
    - required
        - True
    - type
        - list

##### peer1_pcid

???+ "Details"

    - description
        - Port channel identifier of first peer. If this object is not included, then the value defaults to the vPC identifier. This value cannot be changed once vPC is created 
        - Minimum Value (1), Maximum Value (4096) 
        - Default value if not specified is the vPC port identifier
    - type
        - int

##### peer2_access_vlan

???+ "Details"

    - default
        - 
    - description
        - Vlan for the interface of second peer. This option is applicable only for interfaces whose 'mode' is 'access'
    - type
        - str

##### peer2_allowed_vlans

???+ "Details"

    - choices
        - none
        - all
        - vlan-range(e.g., 1-2, 3-40)
    - default
        - none
    - description
        - Vlans that are allowed on this interface of second peer. This option is applicable only for interfaces whose 'mode' is 'trunk'
    - type
        - str

##### peer2_cmds

???+ "Details"

    - default
        - []
    - description
        - Commands to be included in the configuration under this interface of second peer
    - elements
        - str
    - type
        - list

##### peer2_description

???+ "Details"

    - default
        - 
    - description
        - Description of the interface of second peer
    - type
        - str

##### peer2_members

???+ "Details"

    - description
        - Member interfaces that are part of this port channel on second peer
    - elements
        - str
    - required
        - True
    - type
        - list

##### peer2_pcid

???+ "Details"

    - description
        - Port channel identifier of second peer. If this object is not included, then the value defaults to the vPC identifier. This value cannot be changed once vPC is created 
        - Minimum Value (1), Maximum Value (4096) 
        - Default value if not specified is the vPC port identifier
    - type
        - int

##### port_type_fast

???+ "Details"

    - choices
        - True
        - False
    - default
        - True
    - description
        - Spanning-tree edge port behavior
    - type
        - bool

#### switch

???+ "Details"

    - description
        - IP address or DNS name of the management interface. All switches mentioned in this list will be deployed with the included configuration. For vPC interfaces this list object will contain elements each of which is a list of pair of switches
    - elements
        - str
    - required
        - True
    - type
        - list

#### type

???+ "Details"

    - choices
        - pc
        - vpc
        - sub_int
        - lo
        - eth
        - svi
        - st-fex
        - aa-fex
    - description
        - Interface type. Example, pc, vpc, sub_int, lo, eth, svi
    - required
        - True
    - type
        - str
    - type
        - list

### deploy

???+ "Details"

    - default
        - True
    - description
        - Flag indicating if the configuration must be pushed to the switch. This flag is used to decide the deploy behavior in 'deleted' and 'overridden' states as mentioned below 
        - In 'overridden' state this flag will be used to deploy deleted interfaces. 
        - In 'deleted' state this flag will be used to deploy deleted interfaces when a specific 'config' block is not included. 
        - The 'deploy' flags included with individual interface configuration elements under the 'config' block will take precedence over this global flag.
    - type
        - bool

### fabric

???+ "Details"

    - description
        - Name of the target fabric for interface operations
    - required
        - True
    - type
        - str

### override_intf_types

???+ "Details"

    - choices
        - pc
        - vpc
        - sub_int
        - lo
        - eth
        - svi
        - st_fex
        - aa_fex
    - default
        - []
    - description
        - A list of interface types which will be deleted/defaulted in overridden/deleted state. If this list is empty, then during overridden/deleted state, all interface types will be defaulted/deleted. If this list includes specific interface types, then only those interface types that are included in the list will be deleted/defaulted.
    - elements
        - str
    - required
        - False
    - type
        - list

### state

???+ "Details"

    - choices
        - merged
        - replaced
        - overridden
        - deleted
        - query
    - default
        - merged
    - description
        - The required state of the configuration after module completion.
    - type
        - str

## Examples

???+ "Details"

``` yaml
---

# States:
# This module supports the following states:
#
# Merged:
#   Interfaces defined in the playbook will be merged into the target fabric.
#
#   The interfaces listed in the playbook will be created if not already present on the DCNM
#   server. If the interface is already present and the configuration information included
#   in the playbook is either different or not present in DCNM, then the corresponding
#   information is added to the interface on DCNM. If an interface mentioned in playbook
#   is already present on DCNM and there is no difference in configuration, no operation
#   will be performed for such interface.
#
# Replaced:
#   Interfaces defined in the playbook will be replaced in the target fabric.
#
#   The state of the interfaces listed in the playbook will serve as source of truth for the
#   same interfaces present on the DCNM under the fabric mentioned. Additions and updations
#   will be done to bring the DCNM interfaces to the state listed in the playbook.
#   Note: Replace will only work on the interfaces mentioned in the playbook.
#
# Overridden:
#   Interfaces defined in the playbook will be overridden in the target fabric.
#
#   The state of the interfaces listed in the playbook will serve as source of truth for all
#   the interfaces under the fabric mentioned. Additions and deletions will be done to bring
#   the DCNM interfaces to the state listed in the playbook. All interfaces other than the
#   ones mentioned in the playbook will either be deleted or reset to default state.
#   Note: Override will work on the all the interfaces present in the DCNM Fabric.
#
# Deleted:
#   Interfaces defined in the playbook will be deleted in the target fabric.
#
#   Deletes the list of interfaces specified in the playbook.  If the playbook does not include
#   any switches or interface information, then all interfaces from all switches in the
#   fabric will either be deleted or put to default state. If configuuration includes information
#   pertaining to any particular switch, then interfaces belonging to that switch will either be
#   deleted or put to default. If configuration includes both interface and switch information,
#   then the specified interfaces will either be deleted or reset on all the seitches specified
#
# Query:
#   Returns the current DCNM state for the interfaces listed in the playbook.

# LOOPBACK INTERFACE

- name: Create loopback interfaces
  cisco.dcnm.dcnm_interface: &lo_merge
    fabric: mmudigon-fabric
    state: merged                         # only choose from [merged, replaced, deleted, overridden, query]
    config:
      - name: lo100                       # should be of the form lo<port-id>
        type: lo                          # choose from this list [pc, vpc, sub_int, lo, eth]
        switch:
          - "192.172.1.1"                 # provide the switch where to deploy the config
        deploy: true                      # choose from [true, false]
        profile:
          admin_state: true               # choose from [true, false]
          mode: lo                        # choose from [lo]
          int_vrf: ""                     # VRF name
          ipv4_addr: 192.169.10.1         # ipv4 address for the loopback interface
          ipv6_addr: fd01::0201           # ipV6 address for the loopback interface
          route_tag: ""                   # Routing Tag for the interface
          cmds:                           # Freeform config
            - no shutdown
          description: "loopback interface 100 configuration"

- name: Replace loopback interfaces
  cisco.dcnm.dcnm_interface:
    fabric: mmudigon-fabric
    state: replaced                       # only choose from [merged, replaced, deleted, overridden. query]
    config:
      - name: lo100                       # should be of the form lo<port-id>
        type: lo                          # choose from this list [pc, vpc, sub_int, lo, eth]
        switch:
          - "192.172.1.1"                 # provide the switch where to deploy the config
        deploy: true                      ## choose from [true, false]
        profile:
          admin_state: false              ## choose from [true, false]
          mode: lo                        # choose from [lo]
          int_vrf: ""                     # VRF name
          ipv4_addr: 192.169.12.1         ## ipv4 address for the loopback interface
          ipv6_addr: fd01:0203            # ipV6 address for the loopback interface
          route_tag: "100"                ## Routing Tag for the interface
          cmds:                           # Freeform config
            - no shutdown
          description: "loopback interface 100 configuration - replaced"

## Loopback Interfaces Created During Fabric Creation
- name: Mange Fabric loopback interfaces
  cisco.dcnm.dcnm_interface:
    fabric: mmudigon-fabric
    state: merged
    config:
      - name: lo1                           # This is usually lo0 or lo1 created during fabric creation
        type: lo
        switch:
          - "192.172.1.1"                   # provide the switch where to deploy the config
        deploy: true                        # choose from [true, false]
        profile:
          admin_state: false                # choose from [true, false]
          mode: fabric                      # This must be set to 'fabric' for fabric loopback interfaces
          secondary_ipv4_addr: 172.16.5.1   # secondary ipv4 address for loopback interface
          route_tag: "100"                  # Routing Tag for the interface
          cmds:                             # Freeform config
            - no shutdown
          description: "Fabric interface managed by Ansible"

# To delete or reset all interfaces on all switches in the fabric
- name: Delete loopback interfaces
  cisco.dcnm.dcnm_interface:
    fabric: mmudigon-fabric
    state: deleted                        # only choose from [merged, replaced, deleted, overridden, query]

# To delete or reset all interfaces on a specific switch in the fabric
- name: Delete loopback interfaces
  cisco.dcnm.dcnm_interface:
    fabric: mmudigon-fabric
    state: deleted                        # only choose from [merged, replaced, deleted, overridden, query]
    config:
      - switch:
          - "192.172.1.1"                 # provide the switch where to deploy the config

# To delete or reset a particular interface on all switches in the fabric
- name: Delete loopback interfaces
  cisco.dcnm.dcnm_interface:
    fabric: mmudigon-fabric
    state: deleted                        # only choose from [merged, replaced, deleted, overridden, query]
    config:
      - name: lo100                       # should be of the form lo<port-id>

# To delete or reset a particular interface on a specific switch in the fabric
- name: Delete loopback interfaces
  cisco.dcnm.dcnm_interface:
    fabric: mmudigon-fabric
    state: deleted                        # only choose from [merged, replaced, deleted, overridden, query]
    config:
      - name: lo100                       # should be of the form lo<port-id>
        switch:
          - "192.172.1.1"                 # provide the switch where to deploy the config

# To override with a particular interface configuration
- name: Override loopback interfaces
  cisco.dcnm.dcnm_interface:
    fabric: mmudigon-fabric
    state: overridden                     # only choose from [merged, replaced, deleted, overridden, query]
    config:
      - name: lo103                       # should be of the form lo<port-id>
        type: lo                          # choose from this list [pc, vpc, sub_int, lo, eth]
        switch:
          - "192.172.1.1"                 # provide the switch where to deploy the config
        deploy: true                      # choose from [true, false]
        profile:
          admin_state: true               # choose from [true, false]
          mode: lo                        # choose from [lo]
          int_vrf: ""                     # VRF name
          ipv4_addr: 192.169.14.1         # ipv4 address for the loopback interface
          ipv6_addr: fd01::0205           # ipV6 address for the loopback interface
          route_tag: ""                   # Routing Tag for the interface
          cmds:                           # Freeform config
            - no shutdown
          description: "loopback interface 103 configuration - overridden"

# To override all interface on all switches in the fabric
- name: Override loopback interfaces
  cisco.dcnm.dcnm_interface:
    fabric: mmudigon-fabric
    state: overridden                     # only choose from [merged, replaced, deleted, overridden, query]

# To override all interfaces on a particular switche in the fabric
- name: Override loopback interfaces
  cisco.dcnm.dcnm_interface:
    fabric: mmudigon-fabric
    state: overridden                     # only choose from [merged, replaced, deleted, overridden, query]
    config:
      - switch:
          - "192.172.1.1"                 # provide the switch where to deploy the config

# PORTCHANNEL INTERFACE

- name: Create port channel interfaces
  cisco.dcnm.dcnm_interface: &pc_merge
    fabric: mmudigon-fabric
    state: merged                         # only choose from [merged, replaced, deleted, overridden, query]
    config:
      - name: po300                       # should be of the form po<port-id>
        type: pc                          # choose from this list [pc, vpc, sub_int, lo, eth]
        switch:
          - "192.172.1.1"                 # provide the switch information where the config is to be deployed
        deploy: true                      # choose from [true, false]
        profile:
          admin_state: true               # choose from [true, false]
          mode: trunk                     # choose from [trunk, access, l3, monitor]
          members:                        # member interfaces
            - e1/10
          pc_mode: 'on'                   # choose from ['on', 'active', 'passive']
          bpdu_guard: true                # choose from [true, false, no]
          port_type_fast: true            # choose from [true, false]
          mtu: jumbo                      # choose from [default, jumbo]
          allowed_vlans: none             # choose from [none, all, vlan range]
          cmds:                           # Freeform config
            - no shutdown
          description: "port channel acting as trunk"

      - name: po301                       # should be of the form po<port-id>
        type: pc                          # choose from this list [pc, vpc, sub_int, lo, eth]
        switch:
          - "192.172.1.1"                 # provide the switch information where the config is to be deployed
        deploy: true                      # choose from [true, false]
        profile:
          admin_state: false              # choose from [true, false]
          mode: access                    # choose from [trunk, access, l3, monitor]
          members:                        # member interfaces
            - e1/11
          pc_mode: 'on'                   # choose from ['on', 'active', 'passive']
          bpdu_guard: true                # choose from [true, false, no]
          port_type_fast: true            # choose from [true, false]
          mtu: default                    # choose from [default, jumbo]
          access_vlan: 301                #
          cmds:                           # Freeform config
            - no shutdown
          description: "port channel acting as access"

- name: Replace port channel interfaces
  cisco.dcnm.dcnm_interface:
    fabric: mmudigon-fabric
    state: replaced                       # only choose from [merged, replaced, deleted, overridden, query]
    config:
      - name: po300                       # should be of the form po<port-id>
        type: pc                          # choose from this list [pc, vpc, sub_int, lo, eth]
        switch:
          - "192.172.1.1"                 # provide the switch information where the config is to be deployed
        deploy: true                      # choose from [true, false]
        profile:
          admin_state: false              ## choose from [true, false]
          mode: trunk                     # choose from [trunk, access, l3, monitor]
          members:                        # member interfaces
            - e1/10
          pc_mode: 'active'               ## choose from ['on', 'active', 'passive']
          bpdu_guard: false               ## choose from [true, false, no]
          port_type_fast: false           ## choose from [true, false]
          mtu: default                    ## choose from [default, jumbo]
          allowed_vlans: all              ## choose from [none, all, vlan range]
          cmds:                           # Freeform config
            - no shutdown
          description: "port channel acting as trunk - replace"

# To delete or reset a particular interface on a specific switch in the fabric
- name: Delete port channel interfaces
  cisco.dcnm.dcnm_interface:
    fabric: mmudigon-fabric
    state: deleted                        # only choose from [merged, replaced, deleted, overridden, query]
    config:
      - name: po300                       # should be of the form po<port-id>
        switch:
          - "192.172.1.1"                 # provide the switch information where the config is to be deployed

# To delete or reset all interfaces on all switches in the fabric
- name: Delete port channel interfaces
  cisco.dcnm.dcnm_interface:
    fabric: mmudigon-fabric
    state: deleted                        # only choose from [merged, replaced, deleted, overridden, query]

# To delete or reset a particular interface on all switches in the fabric
- name: Delete port-channel interfaces
  cisco.dcnm.dcnm_interface:
    fabric: mmudigon-fabric
    state: deleted                        # only choose from [merged, replaced, deleted, overridden, query]
    config:
      - name: po300                       # should be of the form po<port-id>

# To delete or reset all interfaces on a specific switch in the fabric
- name: Delete port channel interfaces
  cisco.dcnm.dcnm_interface:
    fabric: mmudigon-fabric
    state: deleted                        # only choose from [merged, replaced, deleted, overridden, query]
    config:
      - switch:
          - "192.172.1.1"                 # provide the switch information where the config is to be deployed

- name: Override port channel interfaces
  cisco.dcnm.dcnm_interface:
    fabric: mmudigon-fabric
    state: overridden                     # only choose from [merged, replaced, deleted, overridden, query]
    config:
      - name: po320                       # should be of the form po<port-id>
        type: pc                          # choose from this list [pc, vpc, sub_int, lo, eth]
        switch:
          - "192.172.1.1"                 # provide the switch information where the config is to be deployed
        deploy: true                      # choose from [true, false]
        profile:
          admin_state: true               # choose from [true, false]
          mode: trunk                     # choose from [trunk, access, l3, monitor]
          members:                        # member interfaces
            - e1/10
          pc_mode: 'on'                   # choose from ['on', 'active', 'passive']
          bpdu_guard: true                # choose from [true, false, no]
          port_type_fast: true            # choose from [true, false]
          mtu: jumbo                      # choose from [default, jumbo]
          allowed_vlans: none             # choose from [none, all, vlan range]
          cmds:                           # Freeform config
            - no shutdown
          description: "port channel acting as trunk"

# SUB-INTERFACE

- name: Create sub-interfaces
  cisco.dcnm.dcnm_interface: &sub_merge
    fabric: mmudigon-fabric
    state: merged                         # only choose from [merged, replaced, deleted, overridden, query]
    config:
      - name: eth1/1.1                    # should be of the form eth<port-num>.<port-id>
        type: sub_int                     # choose from this list [pc, vpc, sub_int, lo, eth]
        switch:
          - "192.172.1.1"                 # provide the switch information where the config is to be deployed
        deploy: true                      # choose from [true, false]
        profile:
          admin_state: true               # choose from [true, false]
          mode: subint                    # choose from [subint]
          vlan: 100                       # vlan ID [min:2, max:3967]
          int_vrf: ""                     # VRF name
          ipv4_addr: 192.168.30.1         # ipv4 address for the sub-interface
          ipv4_mask_len: 24               # choose between [min:8, max:31]
          ipv6_addr: fd01::0401           # ipV6 address for the sub-interface
          ipv6_mask_len: 64               # choose between [min:64, max:127]
          mtu: 9216                       # choose between [min:576, max:9216]
          cmds:                           # Freeform config
            - no shutdown
          description: "sub interface eth1/1.1 configuration"

- name: Replace sub-interfaces
  cisco.dcnm.dcnm_interface:
    fabric: mmudigon-fabric
    state: replaced                       # only choose from [merged, replaced, deleted, overridden, query]
    config:
      - name: eth1/1.1                    # should be of the form eth<port-num>.<port-id>
        type: sub_int                     # choose from this list [pc, vpc, sub_int, lo, eth]
        switch:
          - "192.172.1.1"                 # provide the switch information where the config is to be deployed
        deploy: true                      # choose from [true, false]
        profile:
          admin_state: false              ## choose from [true, false]
          mode: subint                    # choose from [subint]
          vlan: 200                       ## vlan ID [min:2, max:3967]
          int_vrf: ""                     # VRF name
          ipv4_addr: 192.168.32.1         ## ipv4 address for the sub-interface
          ipv4_mask_len: 20               # choose between [min:8, max:31]
          ipv6_addr: fd01::0403           # ipV6 address for the sub-interface
          ipv6_mask_len: 64               # choose between [min:64, max:127]
          mtu: 1500                       ## choose between [min:576, max:9216]
          cmds:                           # Freeform config
            - no shutdown
          description: "sub interface eth1/1.1 configuration - replace"

# To delete or reset all interfaces on all switches in the fabric
- name: Delete sub-interfaces
  cisco.dcnm.dcnm_interface:
    fabric: mmudigon-fabric
    state: deleted                        # only choose from [merged, replaced, deleted, overridden, query]

# To delete or reset a particular interface on all switches in the fabric
- name: Delete port-channel interfaces
  cisco.dcnm.dcnm_interface:
    fabric: mmudigon-fabric
    state: deleted                        # only choose from [merged, replaced, deleted, overridden, query]
    config:
      - name: eth1/1.1                    # should be of the form eth<port-num>.<port-id>

- name: Override sub-interfaces
  cisco.dcnm.dcnm_interface:
    fabric: mmudigon-fabric
    state: overridden                     # only choose from [merged, replaced, deleted, overridden, query]
    config:
      - name: eth1/1.3                    # should be of the form eth<port-num>.<port-id>
        type: sub_int                     # choose from this list [pc, vpc, sub_int, lo, eth]
        switch:
          - "192.172.1.1"                 # provide the switch information where the config is to be deployed
        deploy: true                      # choose from [true, false]
        profile:
          admin_state: true               # choose from [true, false]
          mode: subint                    # choose from [subint]
          vlan: 103                       # vlan ID [min:2, max:3967]
          int_vrf: ""                     # VRF name
          ipv4_addr: 192.168.35.1         # ipv4 address for the sub-interface
          ipv4_mask_len: 24               # choose between [min:8, max:31]
          ipv6_addr: fd01::0405           # ipV6 address for the sub-interface
          ipv6_mask_len: 64               # choose between [min:64, max:127]
          mtu: 9216                       # choose between [min:576, max:9216]
          cmds:                           # Freeform config
            - no shutdown
          description: "sub interface eth1/1.3 configuration - override"

# VPC INTERFACE

- name: Create vPC interfaces
  cisco.dcnm.dcnm_interface: &vpc_merge
    fabric: mmudigon-fabric
    state: merged                         # only choose from [merged, replaced, deleted, overridden, query]
    config:
      - name: vpc750                      # should be of the form vpc<port-id>
        type: vpc                         # choose from this list [pc, vpc, sub_int, lo, eth]
        switch:                           # provide switches of vPC pair
          - ["192.172.1.1",
             "192.172.1.2"]
        deploy: true                      # choose from [true, false]
        profile:
          admin_state: true               # choose from [true, false]
          mode: trunk                     # choose from [trunk, access]
          peer1_pcid: 100                 # choose between [Min:1, Max:4096], if not given, will be VPC port-id
          peer2_pcid: 100                 # choose between [Min:1, Max:4096], if not given, will be VPC port-id
          peer1_members:                  # member interfaces on peer 1
            - e1/24
          peer2_members:                  # member interfaces on peer 2
            - e1/24
          pc_mode: 'active'               # choose from ['on', 'active', 'passive']
          bpdu_guard: true                # choose from [true, false, 'no']
          port_type_fast: true            # choose from [true, false]
          mtu: jumbo                      # choose from [default, jumbo]
          peer1_allowed_vlans: none       # choose from [none, all, vlan range]
          peer2_allowed_vlans: none       # choose from [none, all, vlan range]
          peer1_description: "VPC acting as trunk peer1"
          peer2_description: "VPC acting as trunk peer2"


- name: Replace vPC interfaces
  cisco.dcnm.dcnm_interface:
    fabric: mmudigon-fabric
    state: replaced                         # only choose from [merged, replaced, deleted, overridden, query]
    config:
      - name: vpc750                      # should be of the form vpc<port-id>
        type: vpc                         # choose from this list [pc, vpc, sub_int, lo, eth]
        switch:                           # provide switches of vPC pair
          - ["192.172.1.1",
             "192.172.1.2"]
        deploy: true                      # choose from [true, false]
        profile:
          admin_state: false              ## choose from [true, false]
          mode: trunk                     # choose from [trunk, access]
          peer1_pcid: 100                 # choose between [Min:1, Max:4096], if not given, will be VPC port-id
          peer2_pcid: 100                 # choose between [Min:1, Max:4096], if not given, will be VPC port-id
          peer1_members:                  ## member interfaces on peer 1
            - e1/26
          peer2_members:                  ## member interfaces on peer 2
            - e1/26
          pc_mode: 'active'               ## choose from ['on', 'active', 'passive']
          bpdu_guard: false               ## choose from [true, false, 'no']
          port_type_fast: false           ## choose from [true, false]
          mtu: default                    ## choose from [default, jumbo]
          peer1_allowed_vlans: all        ## choose from [none, all, vlan range]
          peer2_allowed_vlans: all        ## choose from [none, all, vlan range]
          peer1_description: "VPC acting as trunk peer1 - modified"
          peer2_description: "VPC acting as trunk peer2 - modified"
          peer1_cmds:                     # Freeform config
              - no shutdown
          peer2_cmds:                     # Freeform config
              - no shutdown

# To delete or reset a particular interface on a specific switch in the fabric
- name: Delete vPC interfaces
  cisco.dcnm.dcnm_interface:
    fabric: mmudigon-fabric
    state: deleted                         # only choose from [merged, replaced, deleted, overridden, query]
    config:
      - name: vpc750                      # should be of the form vpc<port-id>
        switch:                           # provide switches of vPC pair
          - ["192.172.1.1",
             "192.172.1.2"]

- name: Override vPC interfaces
  cisco.dcnm.dcnm_interface:
    fabric: mmudigon-fabric
    state: overridden                         # only choose from [merged, replaced, deleted, overridden, query]
    config:
      - name: vpc752                      # should be of the form vpc<port-id>
        type: vpc                         # choose from this list [pc, vpc, sub_int, lo, eth]
        switch:                           # provide switches of vPC pair
          - ["192.172.1.1",
             "192.172.1.2"]
        deploy: true                      # choose from [true, false]
        profile:
          admin_state: true               # choose from [true, false]
          mode: trunk                     # choose from [trunk, access]
          peer1_pcid: 752                 # choose between [Min:1, Max:4096], if not given, will be VPC port-id
          #peer2_pcid: 1                  # choose between [Min:1, Max:4096], if not given, will be VPC port-id
          peer1_members:                  # member interfaces on peer 1
            - e1/26
          peer2_members:                  # member interfaces on peer 2
            - e1/27
          pc_mode: 'on'                   # choose from ['on', 'active', 'passive']
          bpdu_guard: true                # choose from [true, false, no]
          port_type_fast: true            # choose from [true, false]
          mtu: jumbo                      # choose from [default, jumbo]
          peer1_allowed_vlans: none       # choose from [none, all, vlan range]
          peer2_allowed_vlans: none       # choose from [none, all, vlan range]
          peer1_description: "VPC acting as trunk peer1"
          peer2_description: "VPC acting as trunk peer2"
          peer1_cmds:                     # Freeform config
              - no shutdown
              - no shutdown
          peer2_cmds:                     # Freeform config
              - no shutdown
              - no shutdown

# SVI INTERFACES

- name: Create SVI interfaces including optional parameters
  cisco.dcnm.dcnm_interface:
    check_deploy: true
    fabric: "{{ ansible_svi_fabric }}"
    state: merged                                   # only choose form [merged, replaced, deleted, overridden, query]
    config:
      - name: vlan1001                              # should be of the form vlan<vlan-id>
        type: svi                                   # choose from this list [pc, vpc, sub_int, lo, eth, svi]
        switch:
          - "{{ ansible_switch1 }}"                 # provide the switch information where the config is to be deployed
        deploy: true                                # choose from [true, false]
        profile:
          int_vrf: blue                             # optional, Interface VRF name, default is "default"
          ipv4_addr: 192.168.2.1                    # optional, Interfae IP, default is ""
          ipv4_mask_len: 24                         # optional, IP mask length, default is ""
          mtu: 9216                                 # optional, MTU default is ""
          route_tag: 1001                           # optional, Routing TAG, default is ""
          disable_ip_redirects: true                # optional, flag to enable/disable IP redirects, default is "false"
          cmds:                                     # Freeform config
            - no shutdown
          admin_state: true                         # Flag to enable/disable Vlan interaface
          enable_hsrp: true                         # optional, flag to enable/disable HSRP on the interface, default is "false"
          hsrp_vip: 192.168.2.100                   # optional, Virtual IP address for HSRP, default is ""
          hsrp_group: 10                            # optional, HSRP group, default is ""
          hsrp_priority: 5                          # optional, HSRP priority, default is ""
          hsrp_vmac: 0000.0101.ac0a                 # optional, HSRP virtual MAC, default is ""
          dhcp_server_addr1: 192.200.1.1            # optional, DHCP relay server address, default is ""
          vrf_dhcp1: blue                           # optional, VRF to reach DHCP server. default is ""
          dhcp_server_addr2: 192.200.1.2            # optional, DHCP relay server address, default is ""
          vrf_dhcp2: blue                           # optional, VRF to reach DHCP server. default is ""
          dhcp_server_addr3: 192.200.1.3            # optional, DHCP relay server address, default is ""
          vrf_dhcp3: blue                           # optional, VRF to reach DHCP server. default is ""
          adv_subnet_in_underlay: true              # optional, flag to enable/disable advertisements of subnets into underlay, default is "false"
          enable_netflow: false                     # optional, flag to enable netflow, default is "false"
          netflow_monitor: svi1001                  # optional, name of netflow monitor, default is ""
          hsrp_version: 1                           # optional, HSRP protocol version, default is 1
          preempt: true                             # optional, flag to enable/disable overthrow of low priority active routers, optional is "false"
          mode: vlan                                # choose from [vlan, vlan_admin_state], default is "vlan"
          description: Switched vlan interface 1001 # optional, Interface description, default is ""

- name: Replace SVI interface
  cisco.dcnm.dcnm_interface:
    check_deploy: true
    fabric: "{{ ansible_svi_fabric }}"
    state: replaced                                       # only choose form [merged, replaced, deleted, overridden, query]
    config:
      - name: vlan1001                                    # should be of the form vlan<vlan-id>
        type: svi                                         # choose from this list [pc, vpc, sub_int, lo, eth, svi]
        switch:
          - "{{ ansible_switch1 }}"                       # provide the switch information where the config is to be deployed
        deploy: true                                      # choose from [true, false]
        profile:
          int_vrf: red                                    # optional, Interface VRF name, default is "default"
          ipv4_addr: 192.169.2.1                          # optional, Interfae IP, default is ""
          ipv4_mask_len: 20                               # optional, IP mask length, default is ""
          mtu: 9210                                       # optional, MTU default is ""
          route_tag: 1002                                 # optional, Routing TAG, default is ""
          disable_ip_redirects: false                     # optional, flag to enable/disable IP redirects, default is "false"
          cmds:                                           # Freeform config
            - no shutdown
          admin_state: false                              # Flag to enable/disable Vlan interaface
          enable_hsrp: true                               # optional, flag to enable/disable HSRP on the interface, default is "false"
          hsrp_vip: 192.169.2.100                         # optional, Virtual IP address for HSRP, default is ""
          hsrp_group: 11                                  # optional, HSRP group, default is ""
          hsrp_priority: 5                                # optional, HSRP priority, default is ""
          hsrp_vmac: 0000.0102.ac0a                       # optional, HSRP virtual MAC, default is ""
          dhcp_server_addr1: 193.200.1.1                  # optional, DHCP relay server address, default is ""
          vrf_dhcp1: green                                # optional, VRF to reach DHCP server. default is ""
          dhcp_server_addr2: 193.200.1.2                  # optional, DHCP relay server address, default is ""
          vrf_dhcp2: green                                # optional, VRF to reach DHCP server. default is ""
          dhcp_server_addr3: 193.200.1.3                  # optional, DHCP relay server address, default is ""
          vrf_dhcp3: green                                # optional, VRF to reach DHCP server. default is ""
          adv_subnet_in_underlay: false                   # optional, flag to enable/disable advertisements of subnets into underlay, default is "false"
          enable_netflow: false                           # optional, flag to enable netflow, default is "false"
          netflow_monitor: svi1002                        # optional, name of netflow monitor, default is ""
          hsrp_version: 2                                 # optional, HSRP protocol version, default is 1
          preempt: false                                  # optional, flag to enable/disable overthrow of low priority active routers, optional is "false"
          mode: vlan                                      # choose from [vlan, vlan_admin_state], default is "vlan"
          description: Switched vlan interface 1001 - Rep # optional, Interface description, default is ""

- name: Delete SVI interfaces
  cisco.dcnm.dcnm_interface:
    check_deploy: True
    fabric: "{{ ansible_svi_fabric }}"
    state: deleted                        # only choose form [merged, replaced, deleted, overridden, query]
    config:
      - name: vlan1000                    # should be of the form vlan<vlan-id>
        type: svi                         # choose from this list [pc, vpc, sub_int, lo, eth, svi]
        switch:
          - "{{ ansible_switch1 }}"       # provide the switch where to deploy the config

      - name: vlan1001                    # should be of the form vlan<vlan-id>
        type: svi                         # choose from this list [pc, vpc, sub_int, lo, eth, svi]
        switch:
          - "{{ ansible_switch1 }}"       # provide the switch where to deploy the config

- name: Override SVI interface
  cisco.dcnm.dcnm_interface:
    check_deploy: true
    fabric: "{{ ansible_svi_fabric }}"
    state: overridden                                     # only choose form [merged, replaced, deleted, overridden, query]
    config:
      - name: vlan1002                                    # should be of the form vlan<vlan-id>
        type: svi                                         # choose from this list [pc, vpc, sub_int, lo, eth, svi]
        switch:
          - "{{ ansible_switch1 }}"                       # provide the switch information where the config is to be deployed
        deploy: true                                      # choose from [true, false]
        profile:
          admin_state: true                               # Flag to enable/disable Vlan interaface
          mode: vlan                                      # choose from [vlan, vlan_admin_state], default is "vlan"

# AA FEX INTERFACES

- name: Create AA FEX interfaces including optional parameters
  cisco.dcnm.dcnm_interface:
    check_deploy: True
    fabric: "{{ ansible_svi_fabric }}"
    state: merged                                   # only choose form [merged, replaced, deleted, overridden, query]
    config:
      - name: vpc151                                # should be of the form vpc<id>
        type: aa_fex                                # choose from this list [pc, vpc, sub_int, lo, eth, svi, st_fex, aa_fex]
        switch:
          - "{{ ansible_switch1 }}"                 # provide the switch information where the config is to be deployed
        deploy: true                                # choose from [true, false]
        profile:
          description: "AA FEX interface 151"       # optional, description of FEX interface, default is ""
          peer1_members:                            # optional, member interfaces, default is []
            - e1/10
          peer2_members:                            # optional, member interfaces, default is []
            - e1/10
          mtu: "jumbo"                              # optional, MTU for the interface, default is "jumbo"
          peer1_po_description: "PC 151 for AA FEX" # optional, description of PC interface, default is ""
          peer2_po_description: "PC 151 for AA FEX" # optional, description of PC interface, default is ""
          peer1_cmds:                               # optional, freeform config, default is []
            - no shutdown
          peer2_cmds:                               # optional, freeform config, default is []
            - no shutdown
          admin_state: true                         # Flag to enable/disable FEX interface.
          enable_netflow: false                     # optional, flag to enable netflow, default is false
          mode: port_channel_aa                     # choose from [port_channel_aa], default is "port_channel_aa"

- name: Replace AA FEX interface
  cisco.dcnm.dcnm_interface:
    check_deploy: true
    fabric: "{{ ansible_svi_fabric }}"
    state: replaced                                 # only choose form [merged, replaced, deleted, overridden, query]
    config:
      - name: vpc150                                # should be of the form vpc<id>
        type: aa_fex                                # choose from this list [pc, vpc, sub_int, lo, eth, svi, st_fex, aa_fex]
        switch:
          - "{{ ansible_switch1 }}"                 # provide the switch information where the config is to be deployed
        deploy: true                                # choose from [true, false]
        profile:
          peer1_members:                            # optional, member interfaces, default is []
            - e1/11
          peer2_members:                            # optional, member interfaces, default is []
            - e1/11
          mtu: "default"                            # optional, MTU for the interface, default is "jumbo"
          peer1_po_description: "PC 150 for AA FEX - REP" # optional, description of PC interface, default is ""
          peer2_po_description: "PC 150 for AA FEX - REP" # optional, description of PC interface, default is ""
          admin_state: false                        # Flag to enable/disable FEX interface.
          enable_netflow: false                     # optional, flag to enable netflow, default is false
          mode: port_channel_aa                     # choose from [port_channel_aa], default is "port_channel_aa"

          peer1_cmds:                               # optional, freeform config, default is []
            - ip arp inspection trust
          peer2_cmds:                               # optional, freeform config, default is []
            - ip arp inspection trust

- name: Delete AA FEX interfaces
  cisco.dcnm.dcnm_interface:
    check_deploy: True
    fabric: "{{ ansible_svi_fabric }}"
    state: deleted                        # only choose form [merged, replaced, deleted, overridden, query]
    config:
      - name: vpc151                      # should be of the form vpc<id>
        switch:
          - "{{ ansible_switch1 }}"       # provide the switch where to deploy the config


- name: Overide AA FEX interface with a new one
  cisco.dcnm.dcnm_interface:
    check_deploy: true
    fabric: "{{ ansible_svi_fabric }}"
    state: overridden                               # only choose form [merged, replaced, deleted, overridden, query]
    config:
      - name: vpc151                                # should be of the form vpc<id>
        type: aa_fex                                # choose from this list [pc, vpc, sub_int, lo, eth, svi, st_fex, aa_fex]
        switch:
          - "{{ ansible_switch1 }}"                 # provide the switch information where the config is to be deployed
        deploy: true                                # choose from [true, false]
        profile:
          description: "AA FEX interface 151"       # optional, description of FEX interface, default is ""
          peer1_members:                            # optional, member interfaces, default is []
            - e1/10
          peer2_members:                            # optional, member interfaces, default is []
            - e1/10
          mtu: "jumbo"                              # optional, MTU for the interface, default is "jumbo"
          peer1_po_description: "PC 151 for AA FEX" # optional, description of PC interface, default is ""
          peer2_po_description: "PC 151 for AA FEX" # optional, description of PC interface, default is ""
          peer1_cmds:                               # optional, freeform config, default is []
            - no shutdown
          peer2_cmds:                               # optional, freeform config, default is []
            - no shutdown
          admin_state: true                         # Flag to enable/disable FEX interface.
          enable_netflow: false                     # optional, flag to enable netflow, default is false
          mode: port_channel_aa                     # choose from [port_channel_aa], default is "port_channel_aa"

# STRAIGHT-THROUGH FEX INTERFACES

- name: Create ST FEX interfaces including optional parameters
  cisco.dcnm.dcnm_interface:
    check_deploy: true
    fabric: "{{ ansible_svi_fabric }}"
    state: merged                                   # only choose form [merged, replaced, deleted, overridden, query]
    config:
      - name: po151                                 # should be of the form po<po-id>
        type: st_fex                                # choose from this list [pc, vpc, sub_int, lo, eth, svi, st_fex, aa_fex]
        switch:
          - "{{ ansible_switch1 }}"                 # provide the switch information where the config is to be deployed
        deploy: true                                # choose from [true, false]
        profile:
          description: "ST FEX interface 151"       # optional, description of FEX interface, default is ""
          members:                                  # optional, member interfaces, default is []
            - e1/10
          mtu: "jumbo"                              # optional, MTU for the interface, default is "jumbo"
          po_description: "PC 151 for ST FEX"       # optional, description of PC interface, default is ""
          cmds:                                     # optional, freeform config, default is []
            - no shutdown
          admin_state: true                         # Flag to enable/disable FEX interface.
          enable_netflow: false                     # optional, flag to enable netflow, default is false
          mode: port_channel_st                     # choose from [port_channel_st], default is "port_channel_st"

- name: Replace ST FEX interface
  cisco.dcnm.dcnm_interface:
    check_deploy: true
    fabric: "{{ ansible_svi_fabric }}"
    state: replaced                                 # only choose form [merged, replaced, deleted, overridden, query]
    config:
      - name: po160                                 # should be of the form po<po-id>
        type: st_fex                                # choose from this list [pc, vpc, sub_int, lo, eth, svi, st_fex, aa_fex]
        switch:
          - "{{ ansible_switch1 }}"                 # provide the switch information where the config is to be deployed
          - "{{ ansible_switch2 }}"                 # provide the switch information where the config is to be deployed
        deploy: true                                # choose from [true, false]
        profile:
          members:                                  # optional, member interfaces, default is []
            - e1/11
          mtu: "default"                            # optional, MTU for the interface, default is "jumbo"
          po_description: "PC 160 for ST FEX - REP" # optional, description of PC interface, default is ""
          cmds:                                     # optional, freeform config, default is []
            - ip arp inspection trust
          admin_state: false                        # Flag to enable/disable FEX interface.
          enable_netflow: false                     # optional, flag to enable netflow, default is false
          mode: port_channel_st                     # choose from [port_channel_st], default is "port_channel_st"

- name: Delete ST FEX interfaces
  cisco.dcnm.dcnm_interface:
    check_deploy: True
    fabric: "{{ ansible_svi_fabric }}"
    state: deleted                        # only choose form [merged, replaced, deleted, overridden, query]
    config:
      - name: po159                       # should be of the form po<po-id>
        switch:
          - "{{ ansible_switch1 }}"       # provide the switch where to deploy the config
          - "{{ ansible_switch2 }}"       # provide the switch where to deploy the config

- name: Overide ST FEX interface with a new one
  cisco.dcnm.dcnm_interface:
    check_deploy: true
    fabric: "{{ ansible_svi_fabric }}"
    state: overridden                               # only choose form [merged, replaced, deleted, overridden, query]
    config:
      - name: po151                                 # should be of the form po<po-id>
        type: st_fex                                # choose from this list [pc, vpc, sub_int, lo, eth, svi, st_fex, aa_fex]
        switch:
          - "{{ ansible_switch1 }}"                 # provide the switch information where the config is to be deployed
        deploy: true                                # choose from [true, false]
        profile:
          description: "ST FEX interface 151"       # optional, description of FEX interface, default is ""
          members:                                  # optional, member interfaces, default is []
            - e1/10
          mtu: "jumbo"                              # optional, MTU for the interface, default is "jumbo"
          po_description: "PC 151 for ST FEX"       # optional, description of PC interface, default is ""
          cmds:                                     # optional, freeform config, default is []
            - no shutdown
          admin_state: true                         # Flag to enable/disable FEX interface.
          enable_netflow: false                     # optional, flag to enable netflow, default is false
          mode: port_channel_st                     # choose from [port_channel_st], default is "port_channel_st"

# QUERY

- name: Query interface details
  cisco.dcnm.dcnm_interface:
    fabric: mmudigon-fabric
    state: query            # only choose from [merged, replaced, deleted, overridden, query]
    config:
      - switch:
          - "192.172.1.1"
      - name: po350
        switch:
          - "192.172.1.1"
      - name: lo450
        switch:
          - "192.172.1.1"
      - name: eth1/1
        switch:
          - "192.172.1.1"
      - name: eth1/15.2
        switch:
          - "192.172.1.1"
      - name: vpc750
        switch:
          - "192.172.1.1"

```
