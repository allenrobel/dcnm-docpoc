# dcnm_links

???+ "Details"

    - author
        - Mallik Mudigonda (@mmudigon)
    - description
        - DCNM ansible module for creating, modifying, deleting and querying Links
    - short_description
        - DCNM ansible module for managing Links.
    - version_added
        - 2.1.0


## options

???+ "Details"


### config

???+ "Details"

    - default
        - []
    - description
        - A list of dictionaries containing Links information.
    - elements
        - dict

#### dst_device

???+ "Details"

    - description
        - IP address or DNS name of the destination switch which is part of the link being configured.
    - required
        - True
    - type
        - str

#### dst_fabric

???+ "Details"

    - description
        - Name of the destination fabric. If this is same as 'src_fabric' then the link is considered intra-fabric link. If this parameter is different from 'src_fabric', then the link is considered inter-fabric link.
    - required
        - True
    - type
        - str

#### dst_interface

???+ "Details"

    - description
        - Interface on the destination device which is part of the link being configured.
    - required
        - True
    - type
        - str

#### profile

???+ "Details"

    - description
        - Additional link related parameters that must be included while creating links.

##### admin_state

???+ "Details"

    - description
        - Admin state of the link. 
        - This parameter is not required if template is 'ext_evpn_multisite_overlay_setup', 'ext_multisite_underlay_setup', and 'ext_fabric_setup'.
    - required
        - True
    - type
        - bool

##### auto_deploy

???+ "Details"

    - description
        - Flag that controls auto generation of neighbor VRF Lite configuration for managed neighbor devices. 
        - This parameter is required only if template is 'ext_fabric_setup'.
    - required
        - True
    - type
        - str

##### bgp_multihop

???+ "Details"

    - default
        - 5
    - description
        - eBGP Time-To-Live Value for Remote Peer. 
        - This parameter is required only if template is 'ext_evpn_multisite_overlay_setup'.
    - required
        - False
    - type
        - int

##### dci_routing_proto

???+ "Details"

    - choices
        - is-is
        - ospf
    - default
        - is-is
    - description
        - Routing protocol used on the DCI MPLS link 
        - This parameter is applicable only if template is `ext_vxlan_mpls_underlay_setup` and `mpls_fabric` is `SR`
    - type
        - str

##### dci_routing_tag

???+ "Details"

    - default
        - MPLS_UNDERLAY
    - description
        - Routing Process Tag of DCI Underlay 
        - This parameter is applicable only if template is `ext_vxlan_mpls_underlay_setup`
    - type
        - str

##### deploy_dci_tracking

???+ "Details"

    - default
        - False
    - description
        - Flag to enable deploy DCI tracking. 
        - This parameter is required only if template is 'ext_multisite_underlay_setup'. 
        - This parameter MUST be included only if the fabrics are part of multisite.
    - required
        - False
    - type
        - bool

##### dst_asn

???+ "Details"

    - description
        - BGP ASN number on the destination fabric. 
        - Required for below templates 
        - ext_fabric_setup 
        - ext_multisite_underlay_setup 
        - ext_evpn_multisite_overlay_setup 
        - ext_vxlan_mpls_overlay_setup
    - required
        - True
    - type
        - str

##### ebgp_auth_key_type

???+ "Details"

    - choices
        - 3
        - 7
    - description
        - BGP Key Encryption Type. 
        - This parameter is required only if template is 'ext_multisite_underlay_setup' or 'ext_evpn_multisite_overlay_setup'. 
        - This parameter is required only if inherit_from_msd is false. 
        - Choices are 3 (3DES) or 7 (Cisco)
    - required
        - True
    - type
        - int

##### ebgp_password

???+ "Details"

    - description
        - Encrypted eBGP Password Hex String. 
        - This parameter is required only if template is 'ext_multisite_underlay_setup' or 'ext_evpn_multisite_overlay_setup'. 
        - This parameter is required only if inherit_from_msd is false.
    - required
        - True
    - type
        - str

##### ebgp_password_enable

???+ "Details"

    - default
        - True
    - description
        - Flag to enable eBGP password. 
        - This parameter is required only if template is 'ext_multisite_underlay_setup' or 'ext_evpn_multisite_overlay_setup'.
    - required
        - False
    - type
        - bool

##### enable_macsec

???+ "Details"

    - default
        - False
    - description
        - Enable MACsec on the link. 
        - This parameter is applicable only if MACsec feature is enabled on the fabric. 
        - This parameter is applicable only if template is 'int_intra_fabric_ipv6_link_local' or 'int_intra_fabric_num_link' or 'int_intra_fabric_unnum_link'.
    - required
        - False
    - type
        - bool

##### global_block_range

???+ "Details"

    - default
        - 16000-23999
    - description
        - For Segment Routing binding 
        - This parameter is applicable only if template is `ext_vxlan_mpls_underlay_setup` and `mpls_fabric` is `SR`
    - type
        - str

##### inherit_from_msd

???+ "Details"

    - default
        - True
    - description
        - Flag indicating whether to inherit BGP password from MSD information. 
        - Applicable only when source and destination fabric are in the same MSD fabric. 
        - This parameter is required only if template is 'ext_multisite_underlay_setup' or 'ext_evpn_multisite_overlay_setup'
    - required
        - False
    - type
        - bool

##### intf_vrf

???+ "Details"

    - default
        - 
    - description
        - Name of the non-default VRF for the link. 
        - Make sure to configure the VRF before using it here. 
        - This parameter is applicable only if template is 'int_intra_vpc_peer_keep_alive_link'.
    - required
        - False
    - type
        - str

##### ipv4_address

???+ "Details"

    - description
        - IPV4 address of the source interface without mask. 
        - This parameter is required only if template is 'ext_evpn_multisite_overlay_setup'.
    - required
        - True
    - type
        - str

##### ipv4_subnet

???+ "Details"

    - description
        - IPV4 address of the source interface with mask. 
        - Required for below templates 
        - ext_fabric_setup 
        - ext_multisite_underlay_setup
    - required
        - True
    - type
        - str

##### max_paths

???+ "Details"

    - default
        - 1
    - description
        - Maximum number of iBGP/eBGP paths. 
        - This parameter is required only if template is 'ext_multisite_underlay_setup'.
    - required
        - False
    - type
        - int

##### mpls_fabric

???+ "Details"

    - choices
        - SR
        - LDP
    - default
        - SR
    - description
        - MPLS LDP or Segment-Routing 
        - This parameter is applicable only if template is `ext_vxlan_mpls_underlay_setup`.
    - type
        - str

##### mtu

???+ "Details"

    - description
        - MTU of the link. 
        - This parameter is optional if template is 'ios_xe_int_intra_fabric_num_link'. The default value in this case will be 1500. 
        - This parameter is not required if template is 'ext_evpn_multisite_overlay_setup'.
    - required
        - True
    - type
        - int

##### neighbor_ip

???+ "Details"

    - description
        - IPV4 address of the neighbor switch on the destination fabric. 
        - Required for below templates 
        - ext_fabric_setup 
        - ext_multisite_underlay_setup 
        - ext_evpn_multisite_overlay_setup 
        - ext_vxlan_mpls_underlay_setup 
        - ext_vxlan_mpls_overlay_setup
    - required
        - True
    - type
        - str

##### ospf_area_id

???+ "Details"

    - default
        - 0.0.0.0
    - description
        - OSPF Area ID in IP address format 
        - This parameter is applicable only if template is `ext_vxlan_mpls_underlay_setup` and `dci_routing_proto` is `ospf`
    - type
        - str

##### peer1_bfd_echo_disable

???+ "Details"

    - default
        - False
    - description
        - Enable BFD echo on the source interface. Only applicable if BFD is enabled on the fabric. 
        - This parameter is applicable only if template is 'int_intra_fabric_num_link'.
    - required
        - False
    - type
        - bool

##### peer1_cmds

???+ "Details"

    - default
        - []
    - description
        - Commands to be included in the configuration under the source interface. 
        - This parameter is not required if template is  'ext_evpn_multisite_overlay_setup'.
    - elements
        - str
    - required
        - False
    - type
        - list

##### peer1_description

???+ "Details"

    - default
        - 
    - description
        - Description of the source interface. 
        - This parameter is not required if template is 'ext_evpn_multisite_overlay_setup'.
    - required
        - False
    - type
        - str

##### peer1_ipv4_address

???+ "Details"

    - description
        - IPV4 address of the source interface. 
        - This parameter is optional if the underlying fabric is ipv6 enabled. 
        - This parameter is required only if template is 'int_intra_fabric_num_link' or 'ios_xe_int_intra_fabric_num_link' or 'int_intra_vpc_peer_keep_alive_link'.
    - required
        - True
    - type
        - str

##### peer1_ipv6_address

???+ "Details"

    - default
        - 
    - description
        - IPV6 address of the source interface. 
        - This parameter is required only if the underlying fabric is ipv6 enabled. 
        - This parameter is required only if template is 'int_intra_fabric_num_link' or 'ios_xe_int_intra_fabric_num_link' or 'int_intra_vpc_peer_keep_alive_link'.
    - required
        - False
    - type
        - str

##### peer1_sr_mpls_index

???+ "Details"

    - default
        - 0
    - description
        - Unique SR SID index for the source border 
        - This parameter is applicable only if template is `ext_vxlan_mpls_underlay_setup` and `mpls_fabric` is `SR`
    - type
        - int

##### peer2_bfd_echo_disable

???+ "Details"

    - default
        - False
    - description
        - Enable BFD echo on the destination interface. Only applicable if BFD is enabled on the fabric. 
        - This parameter is applicable only if template is 'int_intra_fabric_num_link'.
    - required
        - False
    - type
        - bool

##### peer2_cmds

???+ "Details"

    - default
        - []
    - description
        - Commands to be included in the configuration under the destination interface. 
        - This parameter is not required if template is 'ext_evpn_multisite_overlay_setup'.
    - elements
        - str
    - required
        - False
    - type
        - list

##### peer2_description

???+ "Details"

    - default
        - 
    - description
        - Description of the destination interface. 
        - This parameter is not required if template is 'ext_evpn_multisite_overlay_setup'.
    - required
        - False
    - type
        - str

##### peer2_ipv4_address

???+ "Details"

    - description
        - IPV4 address of the destination interface. 
        - This parameter is optional if the underlying fabric is ipv6 enabled. 
        - This parameter is required only if template is 'int_intra_fabric_num_link' or 'ios_xe_int_intra_fabric_num_link' or 'int_intra_vpc_peer_keep_alive_link'.
    - required
        - True
    - type
        - str

##### peer2_ipv6_address

???+ "Details"

    - default
        - 
    - description
        - IPV6 address of the destination interface. 
        - This parameter is required only if the underlying fabric is ipv6 enabled. 
        - This parameter is required only if template is 'int_intra_fabric_num_link' or 'ios_xe_int_intra_fabric_num_link' or 'int_intra_vpc_peer_keep_alive_link'.
    - required
        - False
    - type
        - str

##### peer2_sr_mpls_index

???+ "Details"

    - default
        - 0
    - description
        - Unique SR SID index for the destination border 
        - This parameter is applicable only if template is `ext_vxlan_mpls_underlay_setup` and `mpls_fabric` is `SR`
    - type
        - int

##### route_tag

???+ "Details"

    - default
        - 
    - description
        - Routing tag associated with interface IP. 
        - This parameter is required only if template is 'ext_multisite_underlay_setup'
    - type
        - str

##### src_asn

???+ "Details"

    - description
        - BGP ASN number on the source fabric. 
        - Required for below templates 
        - ext_fabric_setup 
        - ext_multisite_underlay_setup 
        - ext_evpn_multisite_overlay_setup 
        - ext_vxlan_mpls_overlay_setup
    - required
        - True
    - type
        - str

##### trm_enabled

???+ "Details"

    - default
        - False
    - description
        - Flag to enable Tenant Routed Multicast. 
        - This parameter is required only if template is 'ext_evpn_multisite_overlay_setup'.
    - required
        - False
    - type
        - bool

#### src_device

???+ "Details"

    - description
        - IP address or DNS name of the source switch which is part of the link being configured.
    - required
        - True
    - type
        - str

#### src_interface

???+ "Details"

    - description
        - Interface on the source device which is part of the link being configured.
    - required
        - True
    - type
        - str

#### template

???+ "Details"

    - choices
        - int_intra_fabric_ipv6_link_local(intra-fabric)
        - int_intra_fabric_num_link (intra-fabric)
        - int_intra_fabric_unnum_link (intra-fabric)
        - int_intra_vpc_peer_keep_alive_link (intra-fabric)
        - int_pre_provision_intra_fabric_link (intra-fabric)
        - ios_xe_int_intra_fabric_num_link (intra-fabric)
        - ext_fabric_setup (inter-fabric)
        - ext_multisite_underlay_setup (inter-fabric)
        - ext_evpn_multisite_overlay_setup (inter-fabric)
    - description
        - Name of the template that is applied on the link being configured. 
        - The last 3 template choices are applicable for inter-fabric links and the others are applicable for intra-fabric links. 
        - This parameter is required only for 'merged' and 'replaced' states. It is 
        - optional for other states.
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
        - Flag to control deployment of links. If set to 'true' then the links included will be deployed to specified switches. If set to 'false', the links will be created but not deployed. 
        - Setting this flag to 'true' will result in all pending configurations on the source and destination devices to be deployed.
    - required
        - False
    - type
        - bool

### src_fabric

???+ "Details"

    - description
        - Name of the source fabric for links operations.
    - required
        - True
    - type
        - str

### state

???+ "Details"

    - choices
        - merged
        - replaced
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

# States:
# This module supports the following states:
#
# Merged:
#   Links defined in the playbook will be merged into the target fabric.
#
#   The links listed in the playbook will be created if not already present on the DCNM
#   server. If the link is already present and the configuration information included
#   in the playbook is either different or not present in DCNM, then the corresponding
#   information is added to the link on DCNM. If a link mentioned in playbook
#   is already present on DCNM and there is no difference in configuration, no operation
#   will be performed for such link.
#
# Replaced:
#   Links defined in the playbook will be replaced in the target fabric.
#
#   The state of the links listed in the playbook will serve as source of truth for the
#   same links present on the DCNM under the fabric mentioned. Additions and updations
#   will be done to bring the DCNM links to the state listed in the playbook.
#   Note: Replace will only work on the links mentioned in the playbook.
#
# Deleted:
#   Links defined in the playbook will be deleted in the target fabric.
#
#   WARNING: Deleting a Link will deploy all pending configurations on the impacted switches
#
# Query:
#   Returns the current DCNM state for the links listed in the playbook. Information included
#    in the playbook will be used as filters to get the desired output.
#
# CREATE LINKS
#
# NUMBERED FABRIC
#
# INTRA-FABRIC

    - name: Create Links
      cisco.dcnm.dcnm_links:
        state: merged                                            # choose from [merged, replaced, deleted, query]
        src_fabric: "ansible_num_fabric"
        config:
          - dst_fabric: "ansible_num_fabric"                     # Destination fabric
            src_interface: "Ethernet1/1"                         # Interface on the Source fabric
            dst_interface: "Ethernet1/1"                         # Interface on the Destination fabric
            src_device: 193.168.1.1                              # Device on the Source fabric
            dst_device: 193.168.1.2                              # Device on the Destination fabric
            template: int_intra_fabric_num_link                  # template to be applied, choose from
                                                                 #   [ int_intra_fabric_ipv6_link_local, int_intra_fabric_num_link,
                                                                 #     int_intra_fabric_unnum_link, int_intra_vpc_peer_keep_alive_link,
                                                                 #     int_pre_provision_intra_fabric_link, ios_xe_int_intra_fabric_num_link ]

            profile:
              peer1_ipv4_addr: 192.168.1.1                       # IP address of the Source interface
              peer2_ipv4_addr: 192.168.1.2                       # IP address of the Destination interface
              admin_state: true                                  # choose from [true, false]
              mtu: 9216                                          #
              peer1_description: "Description of source"         # optional, default is ""
              peer2_description: "Description of dest"           # optional, default is ""
              peer1_bfd_echo_disable: false                      # optional, choose from [true, false]
              peer2_bfd_echo_disable: false                      # optional, choose from [true, false]
              enable_macsec: false                               # optional, choose from [true, false]
              peer1_cmds:                                        # Freeform config for source device
                - no shutdown                                    # optional, default is ""
              peer2_cmds:                                        # Freeform config for destination device
                - no shutdown                                    # optional, default is ""

          - dst_fabric: "ansible_num_fabric"                     # Destination fabric
            src_interface: "Ethernet1/2"                         # Interface on the Source fabric
            dst_interface: "Ethernet1/2"                         # Interface on the Destination fabric
            src_device: 193.168.1.1                              # Device on the Source fabric
            dst_device: 193.168.1.2                              # Device on the Destination fabric
            template: int_pre_provision_intra_fabric_link        # template to be applied, choose from
                                                                 #   [ int_intra_fabric_ipv6_link_local, int_intra_fabric_num_link,
                                                                 #     int_intra_fabric_unnum_link, int_intra_vpc_peer_keep_alive_link,
                                                                 #     int_pre_provision_intra_fabric_link, ios_xe_int_intra_fabric_num_link ]
          - dst_fabric: "ansible_num_fabric"                     # Destination fabric
            src_interface: "Ethernet1/3"                         # Interface on the Source fabric
            dst_interface: "Ethernet1/3"                         # Interface on the Destination fabric
            src_device: 193.168.1.1                              # Device on the Source fabric
            dst_device: 193.168.1.2                              # Device on the Destination fabric
            template: ios_xe_int_intra_fabric_num_link           # template to be applied, choose from
                                                                 #   [ int_intra_fabric_ipv6_link_local, int_intra_fabric_num_link,
                                                                 #     int_intra_fabric_unnum_link, int_intra_vpc_peer_keep_alive_link,
                                                                 #     int_pre_provision_intra_fabric_link, ios_xe_int_intra_fabric_num_link ]

            profile:
              peer1_ipv4_addr: 192.169.2.1                       # IPV4 address of the Source interface
              peer2_ipv4_addr: 192.169.2.2                       # IPV4 address of the Destination interface
              peer1_ipv6_addr: fe80:01::01                       # optional, default is ""
              peer2_ipv6_addr: fe80:01::02                       # optional, default is ""
              admin_state: true                                  # choose from [true, false]
              mtu: 1500                                          # optional, default is 1500
              peer1_description: "Description of source"         # optional, default is ""
              peer2_description: "Description of dest"           # optional, default is ""
              peer1_bfd_echo_disable: false                      # optional, choose from [true, false]
              peer2_bfd_echo_disable: false                      # optional, choose from [true, false]
              enable_macsec: false                               # optional, choose from [true, false]
              peer1_cmds:                                        # Freeform config for source device
                - no shutdown                                    # optional, default is ""
              peer2_cmds:                                        # Freeform config for destination device
                - no shutdown                                    # optional, default is ""
#
# INTER-FABRIC

    - name: Create Links including optional parameters
      cisco.dcnm.dcnm_links: &links_merge_with_opt
        state: merged                                            # choose from [merged, replaced, deleted, query]
        src_fabric: "{{ ansible_num_fabric }}"
        config:
          - dst_fabric: "{{ ansible_unnum_fabric }}"             # Destination fabric
            src_interface: "{{ intf_1_3 }}"                      # Interface on the Source fabric
            dst_interface: "{{ intf_1_3 }}"                      # Interface on the Destination fabric
            src_device: "{{ ansible_num_switch1 }}"              # Device on the Source fabric
            dst_device: "{{ ansible_unnum_switch1 }}"            # Device on the Destination fabric
            template: ext_fabric_setup                           # template to be applied, choose from
                                                                 #   [ ext_fabric_setup, ext_multisite_underlay_setup,
                                                                 #     ext_evpn_multisite_overlay_setup ]
            profile:
              ipv4_subnet: 193.168.1.1/24                        # IP address of interface in src fabric with mask
              neighbor_ip: 193.168.1.2                           # IP address of the interface in dst fabric
              src_asn: 1000                                      # BGP ASN in source fabric
              dst_asn: 1001                                      # BGP ASN in destination fabric
              mtu: 9216                                          #
              auto_deploy: false                                 # optional, default is false
                                                                 # Flag that controls auto generation of neighbor VRF Lite configuration
              peer1_description: "Description of source"         # optional, default is ""
              peer2_description: "Description of dest"           # optional, default is ""
              peer1_cmds:                                        # Freeform config for source interface
                - no shutdown                                    # optional, default is ""
              peer2_cmds:                                        # Freeform config for destination interface
                - no shutdown                                    # optional, default is ""

          - dst_fabric: "{{ ansible_unnum_fabric }}"             # Destination fabric
            src_interface: "{{ intf_1_4 }}"                      # Interface on the Source fabric
            dst_interface: "{{ intf_1_4 }}"                      # Interface on the Destination fabric
            src_device: "{{ ansible_num_switch1 }}"              # Device on the Source fabric
            dst_device: "{{ ansible_unnum_switch1 }}"            # Device on the Destination fabric
            template: ext_multisite_underlay_setup               # template to be applied, choose from
                                                                 #   [ ext_fabric_setup, ext_multisite_underlay_setup,
                                                                 #     ext_evpn_multisite_overlay_setup ]
            profile:
              ipv4_subnet: 193.168.2.1/24                        # IP address of interface in src fabric with mask
              neighbor_ip: 193.168.2.2                           # IP address of the interface in dst fabric
              src_asn: 1200                                      # BGP ASN in source fabric
              dst_asn: 1201                                      # BGP ASN in destination fabric
              mtu: 9216                                          #
              deploy_dci_tracking: false                         # optional, default is false
              max_paths: 1                                       # optional, default is 1
              route_tag: 12345                                   # optional, optional is ""
              ebgp_password_enable: true                         # optional, default is true
              ebgp_password: 0102030405                          # optional, required only if ebgp_password_enable flag is true, and inherit_from_msd
                                                                 # is false.
              inherit_from_msd: True                             # optional, required only if ebgp_password_enable flag is true, default is false
              ebgp_auth_key_type: 3                              # optional, required only if ebpg_password_enable is true, and inherit_from_msd
                                                                 # is false. Default is 3
                                                                 # choose from [3 - 3DES, 7 - Cisco ]
              peer1_description: "Description of source"         # optional, default is ""
              peer2_description: "Description of dest"           # optional, default is ""
              peer1_cmds:                                        # Freeform config for source interface
                - no shutdown                                    # optional, default is ""
              peer2_cmds:                                        # Freeform config for destination interface
                - no shutdown                                    # optional, default is ""

          - dst_fabric: "{{ ansible_unnum_fabric }}"             # Destination fabric
            src_interface: "{{ intf_1_5 }}"                      # Interface on the Source fabric
            dst_interface: "{{ intf_1_5 }}"                      # Interface on the Destination fabric
            src_device: "{{ ansible_num_switch1 }}"              # Device on the Source fabric
            dst_device: "{{ ansible_unnum_switch1 }}"            # Device on the Destination fabric
            template: ext_evpn_multisite_overlay_setup           # template to be applied, choose from
                                                                 #   [ ext_fabric_setup, ext_multisite_underlay_setup,
                                                                 #     ext_evpn_multisite_overlay_setup ]
            profile:
              ipv4_addr: 193.168.3.1                             # IP address of interface in src fabric
              neighbor_ip: 193.168.3.2                           # IP address of the interface in dst fabric
              src_asn: 1300                                      # BGP ASN in source fabric
              dst_asn: 1301                                      # BGP ASN in destination fabric
              trm_enabled: false                                 # optional, default is false
              bgp_multihop: 5                                    # optional, default is 5
              ebgp_password_enable: true                         # optional, default is true
              ebgp_password: 0102030405                          # optional, required only if ebgp_password_enable flag is true, and inherit_from_msd
                                                                 # is false. Default is 3
              inherit_from_msd: false                            # optional, required only if ebgp_password_enable flag is true, default is false
              ebpg_auth_key_type: 3                              # optional, required only if ebpg_password_enable is true, and inherit_from_msd
                                                                 # is false. Default is 3
                                                                 # choose from [3 - 3DES, 7 - Cisco ]
          - dst_fabric: "{{ ansible_unnum_fabric }}"             # Destination fabric
            src_interface: "{{ intf_1_5 }}"                      # Interface on the Source fabric
            dst_interface: "{{ intf_1_5 }}"                      # Interface on the Destination fabric
            src_device: "{{ ansible_num_switch1 }}"              # Device on the Source fabric
            dst_device: "{{ ansible_unnum_switch1 }}"            # Device on the Destination fabric
            template: ext_vxlan_mpls_underlay_setup              # Template of MPLS handoff underlay link
            profile:
              ipv4_subnet: 193.168.3.1/30                        # IP address of interface in src fabric with the mask
              neighbor_ip: 193.168.3.2                           # IP address of the interface in dst fabric
              mpls_fabric: LDP                                   # MPLS handoff protocol, choose from [LDP, SR]
              dci_routing_proto: isis                            # Routing protocol used on the DCI MPLS link, choose from [is-is, ospf]

          - dst_fabric: "{{ ansible_unnum_fabric }}"             # Destination fabric
            src_interface:  Loopback101                          # Loopback interface on the Source fabric
            dst_interface:  Loopback1                            # Loopback interface on the Destination fabric
            src_device: "{{ ansible_num_switch1 }}"              # Device on the Source fabric
            dst_device: "{{ ansible_unnum_switch1 }}"            # Device on the Destination fabric
            template: ext_vxlan_mpls_overlay_setup               #Template of MPLS handoff overlay link
            profile:
              neighbor_ip: 2.2.2.2 .                             # IP address of the loopback interface of destination device
              src_asn: 498278384                                 # BGP ASN in source fabric
              dst_asn: 498278384                                 # BGP ASN in destination fabric



# FABRIC WITH VPC PAIRED SWITCHES

    - name: Create Links
      cisco.dcnm.dcnm_links:
        state: merged                                            # choose from [merged, replaced, deleted, query]
        src_fabric: "ansible_vpc_fabric"
        config:
          - dst_fabric: "ansible_vpc_fabric"                     # Destination fabric
            src_interface: "Ethernet1/4"                         # Interface on the Source fabric
            dst_interface: "Ethernet1/4"                         # Interface on the Destination fabric
            src_device: "ansible_vpc_switch1"                    # Device on the Source fabric
            dst_device: "ansible_vpc_switch2"                    # Device on the Destination fabric
            template: int_intra_vpc_peer_keep_alive_link         # template to be applied, choose from
                                                                 #   [ int_intra_fabric_ipv6_link_local, int_intra_fabric_num_link,
                                                                 #     int_intra_fabric_unnum_link, int_intra_vpc_peer_keep_alive_link,
                                                                 #     int_pre_provision_intra_fabric_link, ios_xe_int_intra_fabric_num_link ]

            profile:
              peer1_ipv4_addr: 192.170.1.1                       # IPV4 address of the Source interface
              peer2_ipv4_addr: 192.170.1.2                       # IPV4 address of the Destination interface
              peer1_ipv6_addr: fe80:2a::01                       # optional, default is ""
              peer2_ipv6_addr: fe80:2a::02                       # optional, default is ""
              admin_state: true                                  # choose from [true, false]
              mtu: 9216                                          #
              peer1_description: "Description of source"         # optional, default is ""
              peer2_description: "Description of dest"           # optional, default is ""
              enable_macsec: false                               # optional, choose from [true, false]
              peer1_cmds:                                        # Freeform config for source device
                - no shutdown                                    # optional, default is ""
              peer2_cmds:                                        # Freeform config for destination device
                - no shutdown                                    # optional, default is ""
              intf_vrf: "test_vrf"                               # optional, default is ""

# UNNUMBERED FABRIC

    - name: Create Links
      cisco.dcnm.dcnm_links:
        state: merged                                            # choose from [merged, replaced, deleted, query]
        src_fabric: "ansible_unnum_fabric"
        config:
          - dst_fabric: "ansible_unnum_fabric"                   # Destination fabric
            src_interface: "Ethernet1/1"                         # Interface on the Source fabric
            dst_interface: "Ethernet1/1"                         # Interface on the Destination fabric
            src_device: "ansible_unnum_switch1"                  # Device on the Source fabric
            dst_device: "ansible_unnum_switch2"                  # Device on the Destination fabric
            template: int_intra_fabric_unnum_link                # template to be applied, choose from
                                                                 #   [ int_intra_fabric_ipv6_link_local, int_intra_fabric_num_link,
                                                                 #     int_intra_fabric_unnum_link, int_intra_vpc_peer_keep_alive_link,
                                                                 #     int_pre_provision_intra_fabric_link, ios_xe_int_intra_fabric_num_link ]

            profile:
              admin_state: true                                  # choose from [true, false]
              mtu: 9216                                          #
              peer1_description: "Description of source"         # optional, default is ""
              peer2_description: "Description of dest"           # optional, default is ""
              enable_macsec: false                               # optional, choose from [true, false]
              peer1_cmds:                                        # Freeform config for source device
                - no shutdown                                    # optional, default is ""
              peer2_cmds:                                        # Freeform config for destination device
                - no shutdown                                    # optional, default is ""

          - dst_fabric: "ansible_unnum_fabric"                   # Destination fabric
            src_interface: "Ethernet1/2"                         # Interface on the Source fabric
            dst_interface: "Ethernet1/2"                         # Interface on the Destination fabric
            src_device: "ansible_unnum_switch1"                  # Device on the Source fabric
            dst_device: "ansible_unnum_switch2"                  # Device on the Destination fabric
            template: int_pre_provision_intra_fabric_link        # template to be applied, choose from
                                                                 #   [ int_intra_fabric_ipv6_link_local, int_intra_fabric_num_link,
                                                                 #     int_intra_fabric_unnum_link, int_intra_vpc_peer_keep_alive_link,
                                                                 #     int_pre_provision_intra_fabric_link, ios_xe_int_intra_fabric_num_link ]

# IPV6 UNDERLAY FABRIC

    - name: Create Links
      cisco.dcnm.dcnm_links:
        state: merged                                            # choose from [merged, replaced, deleted, query]
        src_fabric: "ansible_ipv6_fabric"
        config:
          - dst_fabric: "ansible_ipv6_fabric"                    # Destination fabric
            src_interface: "Ethernet1/1"                         # Interface on the Source fabric
            dst_interface: "Ethernet1/1"                         # Interface on the Destination fabric
            src_device: "ansible_ipv6_switch1"                   # Device on the Source fabric
            dst_device: "ansible_ipv6_switch2"                   # Device on the Destination fabric
            template: int_intra_fabric_ipv6_link_local           # template to be applied, choose from
                                                                 #   [ int_intra_fabric_ipv6_link_local, int_intra_fabric_num_link,
                                                                 #     int_intra_fabric_unnum_link, int_intra_vpc_peer_keep_alive_link,
                                                                 #     int_pre_provision_intra_fabric_link, ios_xe_int_intra_fabric_num_link ]

            profile:
              peer1_ipv4_addr: 192.169.1.1                       # optional, default is ""
              peer2_ipv4_addr: 192.169.1.2                       # optional, default is ""
              peer1_ipv6_addr: fe80:0201::01                     # IP address of the Source interface
              peer2_ipv6_addr: fe80:0201::02                     # IP address of the Source interface
              admin_state: true                                  # choose from [true, false]
              mtu: 9216                                          #
              peer1_description: "Description of source"         # optional, default is ""
              peer2_description: "Description of dest"           # optional, default is ""
              peer1_bfd_echo_disable: false                      # optional, choose from [true, false]
              peer2_bfd_echo_disable: false                      # optional, choose from [true, false]
              enable_macsec: false                               # optional, choose from [true, false]
              peer1_cmds:                                        # Freeform config for source device
                - no shutdown                                    # optional, default is ""
              peer2_cmds:                                        # Freeform config for destination device
                - no shutdown                                    # optional, default is ""

          - dst_fabric: "ansible_ipv6_fabric"                    # Destination fabric
            src_interface: "Ethernet1/2"                         # Interface on the Source fabric
            dst_interface: "Ethernet1/2"                         # Interface on the Destination fabric
            src_device: "ansible_ipv6_switch1"                   # Device on the Source fabric
            dst_device: "ansible_ipv6_switch2"                   # Device on the Destination fabric
            template: int_pre_provision_intra_fabric_link        # template to be applied, choose from
                                                                 #   [ int_intra_fabric_ipv6_link_local, int_intra_fabric_num_link,
                                                                 #     int_intra_fabric_unnum_link, int_intra_vpc_peer_keep_alive_link,
                                                                 #     int_pre_provision_intra_fabric_link, ios_xe_int_intra_fabric_num_link ]
          - dst_fabric: "ansible_ipv6_fabric"                    # Destination fabric
            src_interface: "Ethernet1/3"                         # Interface on the Source fabric
            dst_interface: "Ethernet1/3"                         # Interface on the Destination fabric
            src_device: "ansible_ipv6_switch1"                   # Device on the Source fabric
            dst_device: "ansible_ipv6_switch2"                   # Device on the Destination fabric
            template: int_intra_fabric_num_link                  # template to be applied, choose from
                                                                 #   [ int_intra_fabric_ipv6_link_local, int_intra_fabric_num_link,
                                                                 #     int_intra_fabric_unnum_link, int_intra_vpc_peer_keep_alive_link,
                                                                 #     int_pre_provision_intra_fabric_link, ios_xe_int_intra_fabric_num_link ]

            profile:
              peer1_ipv4_addr: 192.169.2.1                       # IPV4 address of the Source interface
              peer2_ipv4_addr: 192.169.2.2                       # IPV4 address of the Destination interface
              peer1_ipv6_addr: fe80:0202::01                     # IP address of the Source interface
              peer2_ipv6_addr: fe80:0202::02                     # IP address of the Source interface
              admin_state: true                                  # choose from [true, false]
              mtu: 1500                                          # optional, default is 1500
              peer1_description: "Description of source"         # optional, default is ""
              peer2_description: "Description of dest"           # optional, default is ""
              peer1_bfd_echo_disable: false                      # optional, choose from [true, false]
              peer2_bfd_echo_disable: false                      # optional, choose from [true, false]
              enable_macsec: false                               # optional, choose from [true, false]
              peer1_cmds:                                        # Freeform config for source device
                - no shutdown                                    # optional, default is ""
              peer2_cmds:                                        # Freeform config for destination device
                - no shutdown                                    # optional, default is ""
# DELETE LINKS

    - name: Delete Links
      cisco.dcnm.dcnm_links:
        state: deleted                                           # choose from [merged, replaced, deleted, query]
        src_fabric: "ansible_num_fabric"
        config:
          - dst_fabric: "ansible_num_fabric"                     # Destination fabric
            src_interface: "Ethernet1/1"                         # Interface on the Source fabric
            dst_interface: "Ethernet1/1"                         # Interface on the Destination fabric
            src_device: 193.168.1.1                              # Device on the Source fabric
            dst_device: 193.168.1.2                              # Device on the Destination fabric

# QUERY LINKS

    - name: Query Links - with Src Fabric
      cisco.dcnm.dcnm_links:
        state: query                                             # choose from [merged, replaced, deleted, query]
        src_fabric: "ansible_num_fabric"

    - name: Query Links - with Src & Dst Fabric
      cisco.dcnm.dcnm_links:
        state: query                                             # choose from [merged, replaced, deleted, query]
        src_fabric: "ansible_num_fabric"
        config:
          - dst_fabric: "ansible_num_fabric"                     # optional, Destination fabric

    - name: Query Links - with Src & Dst Fabric, Src Intf
      cisco.dcnm.dcnm_links:
        state: query                                             # choose from [merged, replaced, deleted, query]
        src_fabric: "ansible_num_fabric"
        config:
          - dst_fabric: "ansible_num_fabric"                     # optional, Destination fabric
            src_interface: "Ethernet1/1"                         # optional, Interface on the Source fabric

    - name: Query Links - with Src & Dst Fabric, Src & Dst Intf
      cisco.dcnm.dcnm_links:
        state: query                                             # choose from [merged, replaced, deleted, query]
        src_fabric: "ansible_num_fabric"
        config:
          - dst_fabric: "ansible_num_fabric"                     # optional, Destination fabric
            src_interface: "Ethernet1/1"                         # optional, Interface on the Source fabric
            dst_interface: "Ethernet1/1"                         # optional, Interface on the Destination fabric

    - name: Query Links - with Src & Dst Fabric, Src & Dst Intf, Src Device
      cisco.dcnm.dcnm_links:
        state: query                                             # choose from [merged, replaced, deleted, query]
        src_fabric: "ansible_num_fabric"
        config:
          - dst_fabric: "ansible_num_fabric"                     # optional, Destination fabric
            src_interface: "Ethernet1/1"                         # optional, Interface on the Source fabric
            dst_interface: "Ethernet1/1"                         # optional, Interface on the Destination fabric
            src_device: 193.168.1.1                              # optional, Device on the Source fabric
      register: result

    - assert:
        that:
          '(result["response"] | length) >= 1'

    - name: Query Links - with Src & Dst Fabric, Src & Dst Intf, Src & Dst Device
      cisco.dcnm.dcnm_links:
        state: query                                             # choose from [merged, replaced, deleted, query]
        src_fabric: "ansible_num_fabric"
        config:
          - dst_fabric: "ansible_num_fabric"                     # optional, Destination fabric
            src_interface: "Ethernet1/1"                         # optional, Interface on the Source fabric
            dst_interface: "Ethernet1/1"                         # optional, Interface on the Destination fabric
            src_device: 193.168.1.1                              # optional, Device on the Source fabric
            dst_device: 193.168.1.2                              # optional, Device on the Destination fabric
 #
 # INTRA-FABRIC
 #
    - name: Query Links - with Src & Dst Fabric, Src & Dst Intf, Src & Dst Device, Template
      cisco.dcnm.dcnm_links:
        state: query                                             # choose from [merged, replaced, deleted, query]
        src_fabric: "ansible_num_fabric"
        config:
          - dst_fabric: "ansible_num_fabric"                     # optional, Destination fabric
            src_interface: "Ethernet1/1"                         # optional, Interface on the Source fabric
            dst_interface: "Ethernet1/1"                         # optional, Interface on the Destination fabric
            src_device: 193.168.1.1                              # optional, Device on the Source fabric
            dst_device: 193.168.1.2                              # optional, Device on the Destination fabric
            template: int_intra_fabric_num_link                  # optional, template to be applied, choose from
                                                                 #   [ int_intra_fabric_ipv6_link_local, int_intra_fabric_num_link,
                                                                 #     int_intra_fabric_unnum_link, int_intra_vpc_peer_keep_alive_link,
                                                                 #     int_pre_provision_intra_fabric_link, ios_xe_int_intra_fabric_num_link ]
#
# INTER-FABRIC
#
    - name: Query Links - with Src & Dst Fabric, Src & Dst Intf, Src & Dst Device, Template
      cisco.dcnm.dcnm_links:
        state: query                                             # choose from [merged, replaced, deleted, query]
        src_fabric: "{{ ansible_num_fabric }}"
        config:
          - dst_fabric: "{{ ansible_ipv6_fabric }}"              # optional, Destination fabric
            src_interface: "{{ intf_1_6 }}"                      # optional, Interface on the Source fabric
            dst_interface: "{{ intf_1_6 }}"                      # optional, Interface on the Destination fabric
            src_device: "{{ ansible_num_switch1 }}"              # optional, Device on the Source fabric
            dst_device: "{{ ansible_ipv6_switch1 }}"             # optional, Device on the Destination fabric
            template: ext_fabric_setup                           # optional, template to be applied, choose from
                                                                 #   [ ext_fabric_setup, ext_multisite_underlay_setup,
                                                                 #     ext_evpn_multisite_overlay_setup ]
```
