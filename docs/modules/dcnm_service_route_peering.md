# dcnm_service_route_peering

???+ "Details"

    - author
        - Mallik Mudigonda (@mmudigon)
    - description
        - DCNM Ansible Module for Creating, Deleting, Querying and Modifying Route Peerings
    - short_description
        - DCNM Ansible Module for managing Service Route Peerings.
    - version_added
        - 1.2.0


## options

???+ "Details"


### attach

???+ "Details"

    - default
        - True
    - description
        - A flag specifying if the given route peering is to be attached to the specified service node
    - required
        - False
    - type
        - bool

### config

???+ "Details"

    - description
        - A list of dictionaries containing route peering and switch information
    - elements
        - dict

#### deploy_mode

???+ "Details"

    - choices
        - intra_tenant_fw
        - inter_tenant_fw
        - one_arm_adc
        - two_arm_adc
    - description
        - Type of service node.
    - required
        - True
    - type
        - str

#### first_arm

???+ "Details"

    - description
        - Details regarding first arm of the route peering 
        - This parameter is applicable only when 'deploy_mode' is either 'one_arm_adc' or 'two_arm_adc'
    - required
        - True

##### name

???+ "Details"

    - description
        - Network name
    - required
        - True
    - type
        - str

##### profile

???+ "Details"

    - description
        - Profile information for the first arm
    - required
        - True

###### adv_host

???+ "Details"

    - default
        - True
    - description
        - Flag indicating if the host is to be advertised 
        - This parameter is applicable only when 'peering_option' is 'ebgp'
    - required
        - False
    - type
        - bool

###### int_descr

???+ "Details"

    - default
        - 
    - description
        - Description of the interface
    - required
        - False
    - type
        - str

###### ipv4_gw

???+ "Details"

    - description
        - IPV4 gateway information including the mask e.g. 192.168.1.1/24
    - required
        - True
    - type
        - str

###### ipv4_lo

???+ "Details"

    - description
        - IPv4 loopback address 
        - This parameter is applicable only when 'peering_option' is 'ebgp'
    - required
        - True
    - type
        - str

###### ipv4_neighobor

???+ "Details"

    - description
        - IPv4 neighbor address 
        - This parameter is applicable only when 'peering_option' is 'ebgp'
    - required
        - True
    - type
        - str

###### ipv4_vpc_peer_lo

???+ "Details"

    - default
        - 
    - description
        - IPv4 vpc peer loopback address 
        - This parameter is applicable only when 'peering_option' is 'ebgp' This parameter is mandatory if the service node is part of VPC switch pair
    - required
        - False
    - type
        - str

###### ipv6_gw

???+ "Details"

    - default
        - 
    - description
        - IPV6 gateway information including the mask e.g., 2000:01:01::01/64
    - required
        - False
    - type
        - str

###### ipv6_lo

???+ "Details"

    - default
        - 
    - description
        - IPv6 loopback address 
        - This parameter is applicable only when 'peering_option' is 'ebgp'
    - required
        - False
    - type
        - str

###### ipv6_neighbor

???+ "Details"

    - default
        - 
    - description
        - IPv6 neighbor address 
        - This parameter is applicable only when 'peering_option' is 'ebgp'
    - required
        - False
    - type
        - str

###### ipv6_vpc_peer_lo

???+ "Details"

    - default
        - 
    - description
        - IPv6 vpc peer loopback address 
        - This parameter is applicable only when 'peering_option' is 'ebgp' This parameter is mandatory if the service node is part of VPC switch pair
    - required
        - False
    - type
        - str

###### local_asn

???+ "Details"

    - default
        - 12345
    - description
        - Local ASN number 
        - This parameter is applicable only when 'peering_option' is 'ebgp'
    - required
        - False
    - type
        - int

###### neigh_int_descr

???+ "Details"

    - default
        - 
    - description
        - Description of the interface 
        - This parameter is applicable only when 'peering_option' is 'ebgp'
    - required
        - False
    - type
        - str

###### route_map_tag

???+ "Details"

    - default
        - 12345
    - description
        - Route Tag 
        - This parameter is applicable only when 'peering_option' is 'ebgp'
    - type
        - int

###### static_route

???+ "Details"

    - default
        - []
    - description
        - Static route information 
        - This parameter is applicable only when 'peering_option' is 'static'
    - elements
        - dict
    - required
        - False

####### next_hop

???+ "Details"

    - description
        - Gateway IP addresses, for e.g., 192.168.1.1
    - elements
        - str
    - required
        - True
    - type
        - list

####### subnet

???+ "Details"

    - description
        - Subnet information, for e.g., 11.0.0.0/24
    - required
        - True
    - type
        - str
    - type
        - list

###### tag

???+ "Details"

    - default
        - 12345
    - description
        - Route tag information
    - required
        - False
    - type
        - int

###### vlan_name

???+ "Details"

    - default
        - 
    - description
        - Vlan name
    - required
        - False
    - type
        - str
    - type
        - dict

##### vlan_id

???+ "Details"

    - default
        - 0
    - description
        - Vlan Id for the  first arm 
        - If this object is included and if it is already in use, then the module will allocate a new VLAN ID and create the Route Peering. The user provided 'vlan_id' will be ignored.
    - required
        - False
    - type
        - int

##### vrf

???+ "Details"

    - description
        - VRF name for the first arm
    - required
        - True
    - type
        - str
    - type
        - dict

#### inside_network

???+ "Details"

    - description
        - Details regarding inside network of the route peering 
        - This parameter is applicable only when 'deploy_mode' is 'intra_tenant_fw' or 'inter_tenant_fw'
    - required
        - True

##### name

???+ "Details"

    - description
        - Network name
    - required
        - True
    - type
        - str

##### profile

???+ "Details"

    - description
        - Profile information for the inside network
    - required
        - True

###### adv_host

???+ "Details"

    - default
        - True
    - description
        - Flag indicating if the host is to be advertised 
        - This parameter is applicable only when 'peering_option' is 'ebgp'
    - required
        - False
    - type
        - bool

###### int_descr

???+ "Details"

    - default
        - 
    - description
        - Description of the interface
    - required
        - False
    - type
        - str

###### ipv4_gw

???+ "Details"

    - description
        - IPV4 gateway information including the mask e.g. 192.168.1.1/24
    - required
        - True
    - type
        - str

###### ipv4_lo

???+ "Details"

    - description
        - IPv4 loopback address 
        - This parameter is applicable only when 'peering_option' is 'ebgp'
    - required
        - True
    - type
        - str

###### ipv4_neighobor

???+ "Details"

    - description
        - IPv4 neighbor address 
        - This parameter is applicable only when 'peering_option' is 'ebgp'
    - required
        - True
    - type
        - str

###### ipv4_vpc_peer_lo

???+ "Details"

    - default
        - 
    - description
        - IPv4 vpc peer loopback address 
        - This parameter is applicable only when 'peering_option' is 'ebgp'. This parameter is mandatory if the service node is part of VPC switch pair
    - required
        - False
    - type
        - str

###### ipv6_gw

???+ "Details"

    - default
        - 
    - description
        - IPV6 gateway information including the mask e.g., 2000:01:01::01/64
    - required
        - False
    - type
        - str

###### ipv6_lo

???+ "Details"

    - default
        - 
    - description
        - IPv6 loopback address 
        - This parameter is applicable only when 'peering_option' is 'ebgp'
    - required
        - False
    - type
        - str

###### ipv6_neighbor

???+ "Details"

    - default
        - 
    - description
        - IPv6 neighbor address 
        - This parameter is applicable only when 'peering_option' is 'ebgp'
    - required
        - False
    - type
        - str

###### ipv6_vpc_peer_lo

???+ "Details"

    - default
        - 
    - description
        - IPv6 vpc peer loopback address 
        - This parameter is applicable only when 'peering_option' is 'ebgp'. This object is mandatory if the service node switch is part of VPC pair
    - required
        - False
    - type
        - str

###### local_asn

???+ "Details"

    - default
        - 12345
    - description
        - Local ASN number 
        - This parameter is applicable only when 'peering_option' is 'ebgp'
    - required
        - False
    - type
        - int

###### neigh_int_descr

???+ "Details"

    - default
        - 
    - description
        - Description of the interface 
        - This parameter is applicable only when 'peering_option' is 'ebgp'
    - required
        - False
    - type
        - str

###### route_map_tag

???+ "Details"

    - default
        - 12345
    - description
        - Route Tag 
        - This parameter is applicable only when 'peering_option' is 'ebgp'
    - type
        - int

###### static_route

???+ "Details"

    - default
        - []
    - description
        - Static route information 
        - This parameter is applicable only when 'peering_option' is 'static'
    - elements
        - dict
    - required
        - False

####### next_hop

???+ "Details"

    - description
        - Gateway IP addresses, for e.g., 192.168.1.1
    - elements
        - str
    - required
        - True
    - type
        - list

####### subnet

???+ "Details"

    - description
        - Subnet information, for e.g., 11.0.0.0/24
    - required
        - True
    - type
        - str
    - type
        - list

###### tag

???+ "Details"

    - default
        - 12345
    - description
        - Route tag information
    - required
        - False
    - type
        - int

###### vlan_name

???+ "Details"

    - default
        - 
    - description
        - Vlan name
    - required
        - False
    - type
        - str
    - type
        - dict

##### vlan_id

???+ "Details"

    - default
        - 0
    - description
        - Vlan Id for the inside network 
        - If this object is included and if it is already in use, then the module will allocate a new VLAN ID and create the Route Peering. The user provided 'vlan_id' will be ignored.
    - required
        - False
    - type
        - int

##### vrf

???+ "Details"

    - description
        - VRF name for the inside network
    - required
        - True
    - type
        - str
    - type
        - dict

#### name

???+ "Details"

    - description
        - A unique name which identifies the route peering
    - required
        - True
    - type
        - str

#### next_hop

???+ "Details"

    - description
        - Nexthop IPV4 information, e.g., 192.168.1.100 
        - This parameter is applicable only when 'deploy_mode' is 'intra_tenant_fw'
    - required
        - True
    - type
        - int

#### node_name

???+ "Details"

    - description
        - Name of the service node where the route peering is to be deployed
    - required
        - True
    - type
        - str

#### outside_network

???+ "Details"

    - description
        - Details regarding outside network of the route peering 
        - This parameter is applicable only when 'deploy_mode' is 'intra_tenant_fw' or 'inter_tenant_fw'
    - required
        - True

##### name

???+ "Details"

    - description
        - Network name
    - required
        - True
    - type
        - str

##### profile

???+ "Details"

    - description
        - Profile information for the outside network
    - required
        - True

###### adv_host

???+ "Details"

    - default
        - True
    - description
        - Flag indicating if the host is to be advertised 
        - This parameter is applicable only when 'peering_option' is 'ebgp'
    - required
        - False
    - type
        - bool

###### int_descr

???+ "Details"

    - default
        - 
    - description
        - Description of the interface
    - required
        - False
    - type
        - str

###### ipv4_gw

???+ "Details"

    - description
        - IPV4 gateway information including the mask e.g. 192.168.1.1/24
    - required
        - True
    - type
        - str

###### ipv4_lo

???+ "Details"

    - description
        - IPv4 loopback address 
        - This parameter is applicable only when 'peering_option' is 'ebgp'
    - required
        - True
    - type
        - str

###### ipv4_neighobor

???+ "Details"

    - description
        - IPv4 neighbor address 
        - This parameter is applicable only when 'peering_option' is 'ebgp'
    - required
        - True
    - type
        - str

###### ipv4_vpc_peer_lo

???+ "Details"

    - default
        - 
    - description
        - IPv4 vpc peer loopback address 
        - This parameter is applicable only when 'peering_option' is 'ebgp'. This parameter is mandatory if the service node is part of VPC switch pair
    - required
        - False
    - type
        - str

###### ipv6_gw

???+ "Details"

    - default
        - 
    - description
        - IPV6 gateway information including the mask e.g., 2000:01:01::01/64
    - required
        - False
    - type
        - str

###### ipv6_lo

???+ "Details"

    - default
        - 
    - description
        - IPv6 loopback address 
        - This parameter is applicable only when 'peering_option' is 'ebgp'
    - required
        - False
    - type
        - str

###### ipv6_neighbor

???+ "Details"

    - default
        - 
    - description
        - IPv6 neighbor address 
        - This parameter is applicable only when 'peering_option' is 'ebgp'
    - required
        - False
    - type
        - str

###### ipv6_vpc_peer_lo

???+ "Details"

    - default
        - 
    - description
        - IPv6 vpc peer loopback address 
        - This parameter is applicable only when 'peering_option' is 'ebgp' This parameter is mandatory if the service node is part of VPC switch pair
    - required
        - False
    - type
        - str

###### local_asn

???+ "Details"

    - default
        - 12345
    - description
        - Local ASN number 
        - This parameter is applicable only when 'peering_option' is 'ebgp'
    - required
        - False
    - type
        - int

###### neigh_int_descr

???+ "Details"

    - default
        - 
    - description
        - Description of the interface 
        - This parameter is applicable only when 'peering_option' is 'ebgp'
    - required
        - False
    - type
        - str

###### route_map_tag

???+ "Details"

    - default
        - 12345
    - description
        - Route Tag 
        - This parameter is applicable only when 'peering_option' is 'ebgp'
    - type
        - int

###### static_route

???+ "Details"

    - default
        - []
    - description
        - Static route information 
        - This parameter is applicable only when 'peering_option' is 'static' and 'deploy_mode' is 'intra_tenant_fw'
    - elements
        - dict
    - required
        - False

####### next_hop

???+ "Details"

    - description
        - Gateway IP addresses, for e.g., 192.168.1.1
    - elements
        - str
    - required
        - True
    - type
        - list

####### subnet

???+ "Details"

    - description
        - Subnet information, for e.g., 11.0.0.0/24
    - required
        - True
    - type
        - str
    - type
        - list

###### tag

???+ "Details"

    - default
        - 12345
    - description
        - Route tag information
    - required
        - False
    - type
        - int

###### vlan_name

???+ "Details"

    - default
        - 
    - description
        - Vlan name
    - required
        - False
    - type
        - str
    - type
        - dict

##### vlan_id

???+ "Details"

    - default
        - 0
    - description
        - Vlan Id for the outside network 
        - If this object is included and if it is already in use, then the module will allocate a new VLAN ID and create the Route Peering. The user provided 'vlan_id' will be ignored.
    - required
        - False
    - type
        - int

##### vrf

???+ "Details"

    - description
        - VRF name for the outside network
    - required
        - True
    - type
        - str
    - type
        - dict

#### peering_option

???+ "Details"

    - choices
        - static
        - ebgp
    - default
        - static
    - description
        - Specifies the type of peering 
        - This parameter is applicable only when 'deploy_mode' is either 'inter_tenant_fw' or 'one_arm_adc' or 'two_arm_adc'
    - required
        - False
    - type
        - str

#### reverse_next_hop

???+ "Details"

    - default
        - 
    - description
        - Reverse Nexthop IPV4 information, e.g., 192.169.1.100 
        - This parameter is applicable only when 'deploy_mode' is either 'intra_tenant_fw' or 'one_arm_adc' or 'two_arm_adc'
    - required
        - False
    - type
        - str

#### second_arm

???+ "Details"

    - description
        - Details regarding second arm of the route peering 
        - This parameter is applicable only when 'deploy_mode' is either 'one_arm_adc' or 'two_arm_adc'
    - required
        - True

##### name

???+ "Details"

    - description
        - Network name
    - required
        - True
    - type
        - str

##### profile

???+ "Details"

    - description
        - Profile information for the second arm
    - required
        - True

###### int_descr

???+ "Details"

    - default
        - 
    - description
        - Description of the interface
    - required
        - False
    - type
        - str

###### ipv4_gw

???+ "Details"

    - description
        - IPV4 gateway information including the mask e.g. 192.168.1.1/24
    - required
        - True
    - type
        - str

###### ipv6_gw

???+ "Details"

    - default
        - 
    - description
        - IPV6 gateway information including the mask e.g., 2000:01:01::01/64
    - required
        - False
    - type
        - str

###### tag

???+ "Details"

    - default
        - 12345
    - description
        - Route tag information
    - required
        - False
    - type
        - int

###### vlan_name

???+ "Details"

    - default
        - 
    - description
        - Vlan name
    - required
        - False
    - type
        - str
    - type
        - dict

##### vlan_id

???+ "Details"

    - default
        - 0
    - description
        - Vlan Id for the second arm 
        - If this object is included and if it is already in use, then the module will allocate a new VLAN ID and create the Route Peering. The user provided 'vlan_id' will be ignored.
    - required
        - False
    - type
        - int

##### vrf

???+ "Details"

    - description
        - VRF name for the second arm
    - required
        - True
    - type
        - str
    - type
        - dict
    - type
        - list

### deploy

???+ "Details"

    - default
        - True
    - description
        - A flag specifying if a route peering is to be deployed on the switches
    - required
        - False
    - type
        - bool

### fabric

???+ "Details"

    - description
        - Name of the target fabric for route peering operations
    - required
        - True
    - type
        - str

### service_fabric

???+ "Details"

    - description
        - Name of the external fabric attached to the service node for route peering operations
    - required
        - True
    - type
        - str

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
    - required
        - False
    - type
        - str

## Examples

???+ "Details"

``` yaml
---
# L4-L7 Service Insertion:
# =======================
#
# Cisco DCNM has the ability to insert Layer 4-Layer 7 (L4-L7) service devices in a data center fabric, and also enables selectively
# redirecting traffic to these service devices. You can add a service node, create route peering between the service node and the
# service leaf switch, and then selectively redirect traffic to these service nodes. Ansible collections support 3 modules viz.
# Service Node, Service Route Peering and Service Policy to enable this.
#
# Service Node:
#
# You have to create an external fabric and specify that a service node resides in that external fabric during service node creation.
# Service policies are created on the service node to determine the actions to be applied to the traffic
#
# Route Peerings:
#
# Multiple Service Route Peerings can be created under service node. Each Route Peering creates required service networks that is used to
# carry traffic towards the service node.
#
# Service Policy:
#
# Each route peering can have multiple service policies. Service policies can only be created for networks created through route peerings.
# The service policies define the actions to be taken for matching traffic.
#
# Dependency Tree:
#
# Service Node
# |
# |---- Route Peering 1
# |     |
# .     |---- Service Policy 1
# .     |
# .     .
# .     .
# .     .
# .     |---- Service Policy N
# .
# |---- Route Peering N
#       |
#       |---- Service Policy 1
#       |
#       .
#       .
#       .
#       |---- Service Policy N
#
#
# This module supports the following states:

# Merged:
#   Route Peerings defined in the playbook will be merged into the target fabric.
#     - If the Route Peerings does not exist it will be added.
#     - If the Route Peerings exists but properties managed by the playbook are different
#       they will be updated if possible.
#     - Route peerings that are not specified in the playbook will be untouched.
#
# Replaced:
#   Route Peerings defined in the playbook will be replaced in the target fabric.
#     - If the Route Peerings does not exist it will be added.
#     - If the Route Peerings exists but properties managed by the playbook are different
#       they will be updated if possible.
#     - Properties that can be managed by the module but are not specified
#       in the playbook will be deleted or defaulted if possible.
#     - Route Peerings that are not specified in the playbook will be untouched.
#
# Overridden:
#   Route Peerings defined in the playbook will be overridden in the target fabric.
#     - If the Route Peerings does not exist it will be added.
#     - If the Route Peerings exists but properties managed by the playbook are different
#       they will be updated if possible.
#     - Properties that can be managed by the module but are not specified
#       in the playbook will be deleted or defaulted if possible.
#     - Roue Peerings that are not specified in the playbook will be deleted.
#
# Deleted:
#   Route Peerings defined in the playbook will be deleted.
#
# Query:
#   Returns the current DCNM state for the route peerings listed in the playbook.
#
# CREATING ROUTE PEERINGS
# =======================
#
# INTRA-TENANT FIREWALL
# =======================

- name: Create different new service route peerings including all objects
  cisco.dcnm.dcnm_service_route_peering:
    state: merged
    fabric: test-fabric
    service_fabric: external
    attach: true
    deploy: true
    config:
      - name: IT-FW-RP1                                  # mandatory
        node_name: IT-SN-1                               # mandatory
        deploy_mode: intra_tenant_fw                     # mandatory, choices=[intra_tenant_fw, inter_tenant_fw]
        inside_network:                                  #
          vrf: IT-VRF-11                                 # mandatory
          name: rp1-sn1-inside-net                       # mandatory
          vlan_id: 101                                   # optional
          profile:
            ipv4_gw: 192.161.1.1/24                      # mandatory
            ipv6_gw: 2001:db01::1/64                     # optional, default is ''
            vlan_name: rp1-sn1-inside                    # optional, default is ''
            int_descr: "RP1 SN1 inside interface"        # optional, default is ''
            tag: 11111                                   # optional, default is 12345
        next_hop: 192.161.1.100                          # mandatory
        outside_network:                                 #
          vrf: IT-VRF-11                                 # mandatory
          name: rp1-sn1-outside-net                      # mandatory
          vlan_id: 102                                   # optional
          profile:
            ipv4_gw: 192.161.2.1/24                      # mandatory
            ipv6_gw: 2001:db02::1/64                     # optional, default is ''
            vlan_name: rp1-sn1-outside                   # optional, default is ''
            int_descr: "RP1 SN1 outside interface"       # optionL, default is ''
            tag: 11112                                   # optional, default is 12345
        reverse_next_hop: 192.161.2.100                  # optional, default is ''

# INTER-TENANT FIREWALL with STATIC peering
# =========================================

- name: Create different new service route peerings including all objects
  cisco.dcnm.dcnm_service_route_peering:
    state: merged
    fabric: test-fabric
    service_fabric: external
    attach: true
    deploy: true
    config:
      - name: IT-FW-RP2                                  # mandatory
        node_name: IT-SN-1                               # mandatory
        deploy_mode: inter_tenant_fw                     # mandatory, choices=[intra_tenant_fw, inter_tenant_fw]
        peering_option: static                           # optional, default is static, choices=[static, ebgp]
        inside_network:                                  #
          vrf: IT-VRF-21                                 # mandatory
          name: rp2-sn1-inside-net                       # mandatory
          vlan_id: 201                                   # optional
          profile:
            ipv4_gw: 192.162.1.1/24                      # mandatory
            ipv6_gw: 2002:db01::1/64                     # optional, default is ''
            vlan_name: rp2-sn1-inside                    # optional, default is ''
            int_descr: "RP2 SN1 inside interface"        # optional, default is ''
            static_route:                                # optional, default is ''
              - subnet: 20.20.20.0/24
                next_hop:
                  - 120.120.120.100
                  - 121.121.121.100
            tag: 21111                                   # optional, default is 12345
        outside_network:                                 #
          vrf: IT-VRF-22                                 # mandatory
          name: rp2-sn1-outside-net                      # mandatory
          vlan_id: 202                                   # optional
          profile:
            ipv4_gw: 192.162.2.1/24                      # mandatory
            ipv6_gw: 2002:db02::1/64                     # optional, default is ''
            vlan_name: rp2-sn1-outside                   # optional, default is ''
            int_descr: "RP2 SN1 outside interface"       # optional, default is ''
            static_route:                                # optional, default is ''
              - subnet: 21.21.21.0/24
                next_hop:
                  - 122.122.122.100
                  - 123.123.123.100
            tag: 22222                                   # optional, default is 12345

# INTER-TENANT FIREWALL with EBGP peering
# =======================================

- name: Create different new service route peerings including all objects
  cisco.dcnm.dcnm_service_route_peering:
    state: merged
    fabric: test-fabric
    service_fabric: external
    attach: true
    deploy: true
    config:
      - name: IT-FW-RP3                                      # mandatory
        node_name: IT-SN-1                               # mandatory
        deploy_mode: inter_tenant_fw                     # mandatory, choices=[intra_tenant_fw, inter_tenant_fw]
        peering_option: ebgp                             # optional, default is static, choices=[static, ebgp]
        inside_network:
          vrf: IT-VRF-31                                 # mandatory
          name: rp3-sn1-inside-net                       # mandatory
          vlan_id: 301                                   # optional
          profile:
            ipv4_gw: 192.163.1.1/24                      # mandatory
            ipv6_gw: 2003:db01::1/64                     # optional, default is ''
            vlan_name: rp3-sn1-inside                    # optional, default is ''
            int_descr: "RP3 SN1 inside interface"        # optional, default is ''
            tag: 31111                                   # optional, default is 12345
            ipv4_neighbor: 31.31.31.1                    # mandatory
            ipv4_lo: 31.31.31.2                          # mandatory
            ipv4_vpc_peer_lo: 31.31.31.3                 # optional, default is ''
            ipv6_neighbor: 2003:3131::1                  # optional, default is ''
            ipv6_lo: 2003:3132::1                        # optional, default is ''
            ipv6_vpc_peer_lo: 2003:3133::1               # optional, default is ''
            route_map_tag: 33111                         # optional, default is 12345 ????
            neigh_int_descr: "RP3 SN1 inside interface"  # optional, default is '' ????
            local_asn: 65301                             # optional, default is ''
            adv_host: true                               # optional, default is false
        outside_network:
          vrf: IT-VRF-32                                 # mandatory
          name: rp3-sn1-outside-net                      # mandatory
          vlan_id: 302                                   # optional
          profile:
            ipv4_gw: 192.163.2.1/24                      # mandatory
            ipv6_gw: 2003:db02::1/64                     # optional, default is ''
            vlan_name: rp3-sn1-outside                   # optional, default is ''
            int_descr: "RP3 SN1 outside interface"       # optional, default is ''
            tag: 31112                                   # optional, default is 12345
            ipv4_neighbor: 131.131.131.1                 # mandatory
            ipv4_lo: 131.131.131.2                       # mandatory
            ipv4_vpc_peer_lo: 131.131.131.3              # optional, default is ''
            ipv6_neighbor: 2003:8383::1                  # optional, default is ''
            ipv6_lo: 2003:8384::1:100:1                  # optional, default is ''
            ipv6_vpc_peer_lo: 2003:8385::1               # optional, default is ''
            route_map_tag: 31113                         # optional, default is 12345 ????
            neigh_int_descr: "RP3 SN1 outside interface" # optional, default is '' ????
            local_asn: 65302                             # optional, default is ''
            adv_host: true                               # optional, default is false

# ONEARM ADC with EBGP peering
# ============================

- name: Create different new service route peerings including all objects
  cisco.dcnm.dcnm_service_route_peering:
    state: merged
    fabric: test-fabric
    service_fabric: external
    attach: true
    deploy: true
    config:
      - name: IT-ADC-RP4
        node_name: IT-SN-2                               # mandatory
        deploy_mode: one_arm_adc                         # mandatory, choices=[one_arm_adc, two_arm_adc]
        peering_option: ebgp                             # optional, default is static, choices=[static, ebgp]
        first_arm:
          vrf: IT-VRF-41                                 # mandatory
          name: rp4-sn2-first-arm                        # mandatory
          vlan_id: 401                                   # optional
          profile:
            ipv4_gw: 192.164.1.1/24                      # mandatory
            ipv6_gw: 2004:db01::1/64                     # optional, default is ''
            vlan_name: rp4-sn2-first-arm                 # optional, default is ''
            int_descr: "RP4 SN2 first arm intf"          # optional, default is ''
            tag: 41111                                   # optional, default is 12345
            ipv4_neighbor: 41.41.41.1                    # mandatory
            ipv4_lo: 41.41.41.2                          # mandatory
            ipv4_vpc_peer_lo: 41.41.41.3                 # optional, default is ''
            ipv6_neighbor: 2004:4141::1                  # optional, default is ''
            ipv6_lo: 2004:4142::1                        # optional, default is ''
            ipv6_vpc_peer_lo: 2004:4143::1               # optional, default is ''
            route_map_tag: 41112                         # optional, default is 12345
            neigh_int_descr: "RP4 SN2 first arm"         # optional, default is ''
            local_asn: 65401                             # optional, default is ''
            adv_host: true                               # optional, default is false
        reverse_next_hop: 192.164.1.100                  # mandatory

# TWOARM ADC with EBGP peering
# ============================

- name: Create different new service route peerings including all objects
  cisco.dcnm.dcnm_service_route_peering:
    state: merged
    fabric: test-fabric
    service_fabric: external
    attach: true
    deploy: true
    config:
      - name: IT-ADC-RP5
        node_name: IT-SN-2                               # mandatory
        deploy_mode: two_arm_adc                         # mandatory, choices=[one_arm_adc, two_arm_adc]
        peering_option: ebgp                             # optional, default is static, choices=[static, ebgp]
        first_arm:
          vrf: IT-VRF-51            "                    # mandatory
          name: rp5-sn2-first-arm                        # mandatory
          vlan_id: 501                                   # optional
          profile:
            ipv4_gw: 192.165.1.1/24                      # mandatory
            ipv6_gw: 2005:db01::1/64                     # optional, default is ''
            vlan_name: rp5-sn2-first-arm                 # optional, default is ''
            int_descr: "RP5 SN2 first arm intf"          # optional, default is ''
            tag: 51111                                   # optional, default is 12345
            ipv4_neighbor: 51.51.51.1                    # mandatory
            ipv4_lo: 51.51.51.2                          # mandatory
            ipv4_vpc_peer_lo: 51.51.51.3                 # optional, default is ''
            ipv6_neighbor: 2005:5151::1                  # optional, default is ''
            ipv6_lo: 2005:5152::1                        # optional, default is ''
            ipv6_vpc_peer_lo: 2005:5153::1               # optional, default is ''
            route_map_tag: 51115                         # optional, default is 12345
            neigh_int_descr: "RP5 SN2 first arm"         # optional, default is ''
            local_asn: 65501                             # optional, default is ''
            adv_host: true                               # optional, default is false
        second_arm:
          vrf: IT-VRF-52            "                    # mandatory
          name: rp5-sn2-second-arm                       # mandatory
          vlan_id: 502                                   # optional
          profile:
            ipv4_gw: 192.165.2.1/24                      # mandatory
            ipv6_gw: 2005:db02::1/64                     # optional, default is ''
            vlan_name: rp5-sn2-second-arm                # optional, default is ''
            int_descr: "RP5 SN2 second arm intf"         # optional, default is ''
            tag: 51112                                   # optional, default is 12345
        reverse_next_hop: 192.165.1.100                  # mandatory

# ONEARM ADC with STATIC peering
# ==============================

- name: Create different new service route peerings including all objects
  cisco.dcnm.dcnm_service_route_peering:
    state: merged
    fabric: test-fabric
    service_fabric: external
    attach: true
    deploy: true
    config:
      - name: IT-ADC-RP6
        node_name: IT-SN-2                               # mandatory
        deploy_mode: one_arm_adc                         # mandatory, choices=[one_arm_adc, two_arm_adc]
        peering_option: static                           # optional, default is static, choices=[static, ebgp]
        first_arm:
          vrf: IT-VRF-61                                 # mandatory
          name: rp6-sn2-first-arm                        # mandatory
          vlan_id: 601                                   # optional
          profile:
            ipv4_gw: 192.166.1.1/24                      # mandatory
            ipv6_gw: 2006:db01::1/64                     # optional, default is ''
            vlan_name: rp6-sn2-first-arm                 # optional, default is ''
            int_descr: "RP6 SN2 first arm intf"          # optional, default is ''
            tag: 61111                                   # optional, default is 12345
            static_route:                                # optional, default is ''
              - subnet: 61.61.61.1/24
                next_hop:
                  - 161.161.161.1
                  - 162.162.162.1
              - subnet: 22.0.0.0/24
                next_hop:
                  - 163.163.163.1
                  - 164.164.164.1
        reverse_next_hop: 192.166.1.100                  # mandatory

# TWOARM ADC with STATIC peering
# ==============================

- name: Create different new service route peerings including all objects
  cisco.dcnm.dcnm_service_route_peering:
    state: merged
    fabric: test-fabric
    service_fabric: external
    attach: true
    deploy: true
    config:
      - name: IT-ADC-RP7
        node_name: IT-SN-2                               # mandatory
        deploy_mode: two_arm_adc                         # mandatory, choices=[one_arm_adc, two_arm_adc]
        peering_option: static                           # optional, default is static, choices=[static, ebgp]
        first_arm:
          vrf: IT-VRF-71                                 # mandatory
          name: rp7-sn2-first-arm                        # mandatory
          vlan_id: 701                                   # optional
          profile:
            ipv4_gw: 192.167.1.1/24                      # mandatory
            ipv6_gw: 2007:db01::1/64                     # optional, default is ''
            vlan_name: rp7-sn2-first-arm                 # optional, default is ''
            int_descr: "RP6 SN2 first arm  intf"         # optional, default is ''
            tag: 71111                                   # optional, default is 12345
            static_route:                                # optional, default is ''
              - subnet: 71.71.71.1/24
                next_hop:
                  - 171.171.171.1
                  - 172.172.172.1
        second_arm:
          vrf: IT-VRF-72                                 # mandatory
          name: rp7-sn2-second-arm                       # mandatory
          vlan_id: 702                                   # optional
          profile:
            ipv4_gw: 192.167.2.1/24                      # mandatory
            ipv6_gw: 2007:db02::1/64                     # optional, default is ''
            vlan_name: rp7-sn2-second-arm                # optional, default is ''
            int_descr: "RP7 SN2 second arm intf"         # optional, default is ''
            tag: 71112                                   # optional, default is 12345
        reverse_next_hop: 192.167.1.100                  # mandatory

# DELETE ROUTE PEERINGS
# =====================

- name: Delete specific route peerings
  cisco.dcnm.dcnm_service_route_peering:
    state: deleted
    fabric: test-fabric
    service_fabric: external
    config:
      - name: IT-FW-RP1                                   # mandatory
        node_name: IT-SN-1                                # mandatory

- name: Delete all route peerings
  cisco.dcnm.dcnm_service_route_peering:
    state: deleted
    fabric: test-fabric
    service_fabric: external

- name: Delete route peerings with node name
  cisco.dcnm.dcnm_service_route_peering:
    fabric: test-fabric
    service_fabric: external
    state: deleted
    config:
      - node_name: IT-SN-1

# OVERRIDE ROUTE PEERINGS
# =======================

- name: Override existing route peerings with new peerings
  cisco.dcnm.dcnm_service_route_peering:
    state: overridden
    fabric: test-fabric
    service_fabric: external
    attach: true
    deploy: true
    config:
      - name: IT-FW-RP-OVR1                              # mandatory
        node_name: IT-SN-1                               # mandatory
        deploy_mode: intra_tenant_fw                     # mandatory, choices=[intra_tenant_fw, inter_tenant_fw]
        inside_network:                                  #
          vrf: IT-VRF-12                                 # mandatory
          name: rp1-sn1-inside-net-ovr                   # mandatory
          vlan_id: 191                                   # optional
          profile:
            ipv4_gw: 192.161.91.1/24                     # mandatory
            ipv6_gw: 2001:db11::1/64                     # optional, default is ''
            vlan_name: rp1-sn1-inside-ovr                # optional, default is ''
            int_descr: "RP1 SN1 inside interface ovr"    # optional, default is ''
            tag: 11191                                   # optional, default is 12345
        next_hop: 192.161.91.100                         # mandatory
        outside_network:                                 #
          vrf: IT-VRF-12                                 # mandatory
          name: rp1-sn1-outside-net-ovr                  # mandatory
          vlan_id: 192                                   # optional
          profile:
            ipv4_gw: 192.161.92.1/24                     # mandatory
            ipv6_gw: 2001:db12::1/64                     # optional, default is ''
            vlan_name: rp1-sn1-outside-ovr               # optional, default is ''
            int_descr: "RP1 SN1 outside interface ovr"   # optionL, default is ''
            tag: 11192                                   # optional, default is 12345
        reverse_next_hop: 192.161.92.100                 # optional, default is ''

- name: Override existing route peerings with no new peerings
  cisco.dcnm.dcnm_service_route_peering:
    state: overridden
    fabric: test-fabric
    service_fabric: external
    attach: true
    deploy: true

# REPLACE ROUTE PEERINGS
# ======================

- name: Replace service route peerings RP1
  cisco.dcnm.dcnm_service_route_peering: &dcnm_srp_rep_13
    state: replaced
    fabric: test-fabric
    service_fabric: external
    attach: true
    deploy: true
    config:
      - name: IT-FW-RP1                                  # mandatory
        node_name: IT-SN-1                               # mandatory
        deploy_mode: intra_tenant_fw                     # mandatory, choices=[intra_tenant_fw, inter_tenant_fw]
        inside_network:                                  #
          vrf: IT-VRF-11                                 # mandatory
          name: rp1-sn1-inside-net                       # mandatory
          vlan_id: 191                                   # optional
          profile:
            ipv4_gw: 192.161.1.1/24                      # mandatory
            ipv6_gw: 2101:db01::01/64                    # optional, default is ''
            vlan_name: rp1-sn1-inside-rep                # optional, default is ''
            int_descr: "RP1 SN1 inside interface - REP"  # optional, default is ''
            tag: 11101                                   # optional, default is 12345
        next_hop: 192.161.1.200                          # mandatory
        outside_network:                                 #
          vrf: IT-VRF-11                                 # mandatory
          name: rp1-sn1-outside-net                      # mandatory
          vlan_id: 192                                   # optional
          profile:
            ipv4_gw: 192.161.2.1/24                      # mandatory
            ipv6_gw: 2101:db02::1/64                     # optional, default is ''
            vlan_name: rp1-sn1-outside-rep               # optional, default is ''
            int_descr: "RP1 SN1 outside interface- REP"  # optionL, default is ''
            tag: 11102                                   # optional, default is 12345
        reverse_next_hop: 192.161.2.200                  # optional, default is ''

# QUERY ROUTE PEERINGS
# ====================

- name: Query existing route peerings with specific peering names
  cisco.dcnm.dcnm_service_route_peering:
    state: query
    fabric: test-fabric
    service_fabric: external
    config:
      - name: IT-FW-RP1                                   # optional
        node_name: IT-SN-1                                # mandatory

      - name: IT-FW-RP2                                   # optional
        node_name: IT-SN-1                                # mandatory

      - name: IT-FW-RP3                                   # optional
        node_name: IT-SN-1                                # mandatory

      - name: IT-ADC-RP4                                  # optional
        node_name: IT-SN-2                                # mandatory

      - name: IT-ADC-RP5                                  # optional
        node_name: IT-SN-2                                # mandatory

      - name: IT-ADC-RP6                                  # optional
        node_name: IT-SN-2                                # mandatory

      - name: IT-ADC-RP7                                  # optional
        node_name: IT-SN-2                                # mandatory

- name: Query existing route peerings without specific peering names
  cisco.dcnm.dcnm_service_route_peering:
    state: query
    fabric: test-fabric
    service_fabric: external
    config:
        node_name: IT-SN-1                                # mandatory

```
