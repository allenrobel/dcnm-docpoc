# dcnm_vpc_pair

???+ "Details"

    - author
        - Mallik Mudigonda(@mmudigon)
    - description
        - DCNM Ansible Module for managing VPC switch pairs.
    - short_description
        - DCNM Ansible Module for managing VPC switch pairs required for VPC interfaces.
    - version_added
        - 3.5.0


## options

???+ "Details"


### config

???+ "Details"

    - default
        - []
    - description
        - A list of dictionaries containing VPC switch pair information
    - elements
        - dict

#### peerOneId

???+ "Details"

    - description
        - IP Address/Host Name of Peer1 of VPC switch pair.
    - required
        - True
    - type
        - str

#### peerTwoId

???+ "Details"

    - description
        - IP Address/Host Name of Peer2 of VPC switch pair.
    - required
        - True
    - type
        - str

#### profile

???+ "Details"

    - description
        - A dictionary of additional VPC switch pair related parameters that must be included while creating VPC switch pairs.

##### ADMIN_STATE

???+ "Details"

    - description
        - Flag to enable/disbale administrative state of the interface.
    - required
        - True
    - type
        - bool

##### ALLOWED_VLANS

???+ "Details"

    - choices
        - none
        - all
        - vlan-range(e.g., 1-2, 3-40)
    - default
        - all
    - description
        - Vlans that are allowed on the VPC peer link port-channel.
    - type
        - str

##### DOMAIN_ID

???+ "Details"

    - description
        - VPC domain ID. 
        - Minimum value is 1 and Maximum value is 1000.
    - required
        - True
    - type
        - int

##### FABRIC_NAME

???+ "Details"

    - description
        - Name of the target fabric for VPC switch pair operations.
    - required
        - True
    - type
        - str

##### KEEP_ALIVE_HOLD_TIMEOUT

???+ "Details"

    - default
        - 3
    - description
        - Hold timeout to ignore stale peer keep alive messages. 
        - Minimum value is 3 and Maximum value is 10
    - type
        - int

##### KEEP_ALIVE_VRF

???+ "Details"

    - description
        - Name of the VRF used for keep-alive messages.
    - required
        - True
    - type
        - str

##### PC_MODE

???+ "Details"

    - choices
        - on
        - active
        - passive
    - default
        - active
    - description
        - Port channel mode.
    - type
        - str

##### PEER1_DOMAIN_CONF

???+ "Details"

    - default
        - 
    - description
        - Additional CLI for PEER1 vPC Domain.
    - type
        - str

##### PEER1_KEEP_ALIVE_LOCAL_IP

???+ "Details"

    - description
        - IP address of a L3 interface in non-default VRF on PEER1.
    - required
        - True
    - type
        - str

##### PEER1_MEMBER_INTERFACES

???+ "Details"

    - default
        - []
    - description
        - A list of member interfaces for PEER1.
    - elements
        - str
    - type
        - list

##### PEER1_PCID

???+ "Details"

    - default
        - 1
    - description
        - PEER1 peerlink port-channel number. 
        - Minimum value is 1 and Maximum value is 4096.
    - type
        - int

##### PEER1_PO_CONF

???+ "Details"

    - default
        - 
    - description
        - Additional CLI for PEER1 vPC peerlink port-channel.
    - type
        - str

##### PEER1_PO_DESC

???+ "Details"

    - default
        - 
    - description
        - Description for the PEER1 port-channel. 
        - Minimum length is 1 and Maximum length is 254.
    - type
        - str

##### PEER2_DOMAIN_CONF

???+ "Details"

    - default
        - 
    - description
        - Additional CLI for PEER2 vPC Domain.
    - type
        - str

##### PEER2_KEEP_ALIVE_LOCAL_IP

???+ "Details"

    - description
        - IP address of a L3 interface in non-default VRF on PEER2.
    - required
        - True
    - type
        - str

##### PEER2_MEMBER_INTERFACES

???+ "Details"

    - default
        - []
    - description
        - A list of member interfaces for PEER2.
    - elements
        - str
    - type
        - list

##### PEER2_PCID

???+ "Details"

    - default
        - 1
    - description
        - PEER2 peerlink port-channel number. 
        - Minimum value is 1 and Maximum value is 4096.
    - type
        - int

##### PEER2_PO_CONF

???+ "Details"

    - default
        - 
    - description
        - Additional CLI for PEER2 vPC peerlink port-channel.
    - type
        - str

##### PEER2_PO_DESC

???+ "Details"

    - default
        - 
    - description
        - Description for the PEER2 port-channel. 
        - Minimum length is 1 and Maximum length is 254.
    - type
        - str

#### templateName

???+ "Details"

    - description
        - Name of the template which inlcudes the required parameters for creating the VPC switch pair. 
        - This parameter is 'mandatory' if the fabric is of type 'LANClassic' or 'External'. It is optional otherwise.
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
        - Flag indicating if the configuration must be pushed to the switch.
    - type
        - bool

### src_fabric

???+ "Details"

    - description
        - Name of the target fabric for VPC switch pair operations
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
        - fetch
    - default
        - merged
    - description
        - The required state of the configuration after module completion.
    - type
        - str

### templates

???+ "Details"

    - default
        - []
    - description
        - List of templates to be fetched. 
        - This is required only if the 'state' is 'fetch'. In this case the list should contain the template names whose details. are to be fetched.
    - elements
        - str
    - type
        - list

## Examples

???+ "Details"

``` yaml
---

# States:
# This module supports the following states:
#
# Merged:
#   VPC switch pairs defined in the playbook will be merged into the target fabric.
#
#   The VPC switch pairs listed in the playbook will be created if not already present on the DCNM
#   server. If the VPC switch pair is already present and the configuration information included
#   in the playbook is either different or not present in DCNM, then the corresponding
#   information is added to the DCNM. If a VPC switch pair  mentioned in playbook
#   is already present on DCNM and there is no difference in configuration, no operation
#   will be performed for such switch pairs.
#
# Replaced:
#   VPC switch pairs defined in the playbook will be replaced in the target fabric.
#
#   The state of the VPC switch pairs listed in the playbook will serve as source of truth for the
#   same VPC switch pairs present on the DCNM under the fabric mentioned. Additions and updations
#   will be done to bring the DCNM VPC switch pairs to the state listed in the playbook.
#   Note: Replace will only work on the VPC switch pairs mentioned in the playbook.
#
# Overridden:
#   VPC switch pairs defined in the playbook will be overridden in the target fabric.
#
#   The state of the VPC switch pairs listed in the playbook will serve as source of truth for all
#   the VPC switch pairs under the fabric mentioned. Additions and deletions will be done to bring
#   the DCNM VPC switch pairs to the state listed in the playbook. All VPC switch pairs other than the
#   ones mentioned in the playbook will be deleted.
#   Note: Override will work on the all the VPC switch pairs present in the DCNM Fabric.
#
# Deleted:
#   VPC switch pairs defined in the playbook will be deleted in the target fabric.
#
#   Deletes the list of VPC switch pairs specified in the playbook.  If the playbook does not include
#   any VPC switch pair information, then all VPC switch pairs from the fabric will be deleted.
#
# Query:
#   Returns the current DCNM state for the VPC switch pairs listed in the playbook.

# CREATE VPC SWITCH PAIR (LANClassic or External fabrics)

- name: Merge VPC switch pair paremeters
  cisco.dcnm.dcnm_vpc_pair:
    src_fabric: "test-fabric"
    deploy: true
    state: merged
    config:
      - peerOneId: 192.168.1.1
        peerTwoId: 192.168.1.2
        templateName: "vpc_pair"
        profile:
          ADMIN_STATE: True
          ALLOWED_VLANS: "all"
          DOMAIN_ID: 100
          FABRIC_NAME: test-fabric
          KEEP_ALIVE_HOLD_TIMEOUT: 3
          KEEP_ALIVE_VRF: management
          PC_MODE: active
          PEER1_DOMAIN_CONF: "graceful consistency-check"
          PEER1_KEEP_ALIVE_LOCAL_IP: 192.168.1.1
          PEER1_MEMBER_INTERFACES: e1/21,e1/22-23
          PEER1_PCID: 101
          PEER1_PO_CONF: "buffer-boost"
          PEER1_PO_DESC: "This is peer1 PC"
          PEER2_DOMAIN_CONF: "graceful consistency-check"
          PEER2_KEEP_ALIVE_LOCAL_IP: 192.168.1.2
          PEER2_MEMBER_INTERFACES: e1/21,e1/22-23
          PEER2_PCID: 102
          PEER2_PO_CONF: "buffer-boost"
          PEER2_PO_DESC: "This is peer2 PC"

# CREATE VPC SWITCH PAIR (VXLAN fabrics)

- name: Merge VPC switch pair paremeters
  cisco.dcnm.dcnm_vpc_pair:
    src_fabric: "test-fabric"
    deploy: true
    state: merged
    config:
      - peerOneId: 192.168.1.1
        peerTwoId: 192.168.1.2

# DELETE VPC SWITCH PAIR

- name: Delete VPC switch pair
  cisco.dcnm.dcnm_vpc_pair:
    src_fabric: "test-fabric"
    deploy: true
    state: deleted
    config:
      - peerOneId: 192.168.1.1
        peerTwoId: 192.168.1.2

# REPLACE VPC SWITCH PAIR (LANClassic or External fabrics)

- name: Replace VPC switch pair paremeters
  cisco.dcnm.dcnm_vpc_pair:
    src_fabric: "test-fabric"
    deploy: true
    state: merged
    config:
      - peerOneId: 192.168.1.1
        peerTwoId: 192.168.1.2
        templateName: "vpc_pair"
        profile:
          ADMIN_STATE: True
          ALLOWED_VLANS: "all"
          DOMAIN_ID: 100
          FABRIC_NAME: test-fabric
          KEEP_ALIVE_HOLD_TIMEOUT: 3
          KEEP_ALIVE_VRF: management
          PC_MODE: active
          PEER1_DOMAIN_CONF: "graceful consistency-check"
          PEER1_KEEP_ALIVE_LOCAL_IP: 192.168.1.1
          PEER1_MEMBER_INTERFACES: e1/21,e1/22-23
          PEER1_PCID: 101
          PEER1_PO_CONF: "buffer-boost"
          PEER1_PO_DESC: "This is peer1 PC"
          PEER2_DOMAIN_CONF: "graceful consistency-check"
          PEER2_KEEP_ALIVE_LOCAL_IP: 192.168.1.2
          PEER2_MEMBER_INTERFACES: e1/21,e1/22-23
          PEER2_PCID: 102
          PEER2_PO_CONF: "buffer-boost"
          PEER2_PO_DESC: "This is peer2 PC"

# OVERRIDDE VPC SWITCH PAIRS

- name: Override with a new VPC switch pair
  cisco.dcnm.dcnm_vpc_pair:
    src_fabric: "test-fabric"
    deploy: true
    state: overridden
    config:
      - peerOneId: 192.168.1.1
        peerTwoId: 192.168.1.2
        templateName: "vpc_pair"
        profile:
          ADMIN_STATE: True
          ALLOWED_VLANS: "all"
          DOMAIN_ID: 100
          FABRIC_NAME: "test-fabric"
          KEEP_ALIVE_HOLD_TIMEOUT: 3
          KEEP_ALIVE_VRF: management
          PC_MODE: active
          PEER1_KEEP_ALIVE_LOCAL_IP: 192.168.1.1
          PEER1_MEMBER_INTERFACES: e1/20
          PEER1_PCID: 101
          PEER1_PO_DESC: "This is peer1 PC"
          PEER2_KEEP_ALIVE_LOCAL_IP: 192.168.1.2
          PEER2_MEMBER_INTERFACES: e1/20
          PEER2_PCID: 102
          PEER2_PO_DESC: "This is peer2 PC"

- name: Override without any new switch pairs
  cisco.dcnm.dcnm_vpc_pair:
    src_fabric: "test-fabric"
    deploy: true
    state: overridden

# QUERY VPC SWITCH PAIRS

- name: Query VPC switch pairs - with no filters
  cisco.dcnm.dcnm_vpc_pair:
    src_fabric: "test-fabric"
    state: query

- name: Query VPC switch pairs - with both peers specified
  cisco.dcnm.dcnm_vpc_pair:
    src_fabric: "test-fabric"
    state: query
    config:
      - peerOneId: "{{ ansible_switch1 }}"
        peerTwoId: "{{ ansible_switch2 }}"

- name: Query VPC switch pairs - with one peer specified
  cisco.dcnm.dcnm_vpc_pair:
    src_fabric: "test-fabric"
    state: query
    config:
      - peerOneId: "{{ ansible_switch1 }}"
```
