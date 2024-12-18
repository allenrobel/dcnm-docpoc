# dcnm_service_node

???+ "Details"

    - author
        - Karthik Babu Harichandra Babu(@kharicha)
    - description
        - Create/Modify/Delete service node based on type and attached interfaces from a DCNM managed VXLAN fabric.
    - short_description
        - Create/Modify/Delete service node based on type and attached interfaces from a DCNM managed VXLAN fabric.
    - version_added
        - 1.2.0


## options

???+ "Details"


### config

???+ "Details"

    - description
        - List of details of service nodes being managed. Not required for state deleted
    - elements
        - dict

#### attach_interface

???+ "Details"

    - description
        - List of switch interfaces where the service node will be attached
    - required
        - True
    - type
        - str

#### form_factor

???+ "Details"

    - choices
        - physical
        - virtual
    - default
        - physical
    - description
        - Name of the form factor of the service node
    - type
        - str

#### name

???+ "Details"

    - description
        - Name of service node
    - required
        - True
    - type
        - str

#### svc_int_name

???+ "Details"

    - description
        - Name of the service interface
    - required
        - True
    - type
        - str

#### switches

???+ "Details"

    - description
        - IP address of the switch where service node will be added/deleted
    - elements
        - str
    - required
        - True
    - type
        - list

#### type

???+ "Details"

    - choices
        - firewall
        - load_balancer
        - virtual_network_function
    - default
        - firewall
    - description
        - Service node type
    - type
        - str
    - type
        - list

### fabric

???+ "Details"

    - description
        - Name of attached easy fabric to which service node is attached
    - required
        - True
    - type
        - str

### service_fabric

???+ "Details"

    - description
        - Name of external fabric where the service node is located
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
        - The state of DCNM after module completion.
    - type
        - str

## Examples

???+ "Details"

``` yaml
---
# L4-L7 Service Insertion:
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
# This module supports the following states:
#
# Merged:
#   Service Nodes defined in the playbook will be merged into the service fabric.
#     - If the service node does not exist it will be added.
#     - If the service node exists but properties managed by the playbook are different
#       they will be updated if possible.
#     - Service Nodes that are not specified in the playbook will be untouched.
#
# Replaced:
#   Service Nodes defined in the playbook will be replaced in the service fabric.
#     - If the service node does not exist it will be added.
#     - If the service node exists but properties managed by the playbook are different
#       they will be updated if possible.
#     - Properties that can be managed by the module but are not specified
#       in the playbook will be deleted or defaulted if possible.
#     - Service Nodes that are not specified in the playbook will be untouched.
#
# Overridden:
#   Service Node defined in the playbook will be overridden in the service fabric.
#     - If the service node does not exist it will be added.
#     - If the service node exists but properties managed by the playbook are different
#       they will be updated if possible.
#     - Properties that can be managed by the module but are not specified
#       in the playbook will be deleted or defaulted if possible.
#     - Service Nodes that are not specified in the playbook will be deleted.
#
# Deleted:
#   Service Node defined in the playbook will be deleted.
#   If no Service Nodes are provided in the playbook, all service node present on that DCNM fabric will be deleted.
#
# Query:
#   Returns the current DCNM state for the service node listed in the playbook.

- name: Merge Service Nodes
  cisco.dcnm.dcnm_service_node:
    fabric: Fabric1
    service_fabric: external
    state: merged
    config:
    - name: SN-11
      type: firewall
      form_factor: virtual
      svc_int_name: svc1
      attach_interface: Ethernet1/1
      switches:
      - 192.168.1.224
    - name: SN-12
      type: firewall
      form_factor: virtual
      svc_int_name: svc1
      attach_interface: vPC1
      switches:  # up to two switches, if two switches are provided, vpc is only option
      - 192.168.1.224
      - 192.168.1.225

- name: Replace Service Nodes form factor/type parameter
  cisco.dcnm.dcnm_service_node:
    fabric: Fabric1
    service_fabric: external
    state: replaced
    config:
    - name: SN-11
      type: firewall
   #  Replace can only modify the form factor
   #  form_factor: virtual  # the virtual will be changed to new physical
   #  form_factor: physical
      svc_int_name: svc1
      attach_interface: Ethernet1/1
      switches:
      - 192.168.1.224
   #   Nothing will be replaced in the below service node as there is no change
   #   Dont touch this if its present on DCNM
   # - name: SN-12
   #   type: firewall
   #   form_factor: virtual
   #   svc_int_name: svc1
   #   attach_interface: vPC1
   #   switches:  # up to two switches, if two switches are provided, vpc is only option
   #   - 192.168.1.224
   #   - 192.168.1.225

- name: Override Service Nodes
  cisco.dcnm.dcnm_service_node:
    fabric: Fabric1
    service_fabric: external
    state: overridden
    config:
   # Create this service node
    - name: SN-13
      type: firewall
      form_factor: virtual
      svc_int_name: svc1
      attach_interface: Ethernet1/1
      switches:
      - 192.168.1.224
   # Delete this service node from the DCNM
   # - name: SN-11
   #   type: firewall
   #   form_factor: virtual
   #   svc_int_name: svc1
   #   attach_interface: Ethernet1/1
   #   switches:
   #   - 192.168.1.224
   # Delete this service node from the DCNM
   # - name: SN-12
   #   type: firewall
   #   form_factor: virtual
   #   svc_int_name: svc1
   #   attach_interface: vPC1
   #   switches:  # up to two switches, if two switches are provided, vpc is only option
   #   - 192.168.1.224
   #   - 192.168.1.225

- name: Delete selected Service Nodes
  cisco.dcnm.dcnm_service_node:
    fabric: Fabric1
    service_fabric: external
    state: deleted
    config:
    - name: SN-11
      type: firewall
      form_factor: virtual
      svc_int_name: svc1
      attach_interface: Ethernet1/1
      switches:
      - 192.168.1.224
    - name: SN-12
      type: firewall
      form_factor: virtual
      svc_int_name: svc1
      attach_interface: vPC1
      switches:  # up to two switches, if two switches are provided, vpc is only option
      - 192.168.1.224
      - 192.168.1.225

- name: Delete all the Service Nodes
  cisco.dcnm.dcnm_service_node:
    fabric: Fabric1
    service_fabric: external
    state: deleted

- name: Query Service Nodes state for SN-11 and SN-12
  cisco.dcnm.dcnm_service_node:
    fabric: Fabric1
    service_fabric: external
    state: query
    config:
    - name: SN-11
      type: firewall
      form_factor: virtual
      svc_int_name: svc1
      attach_interface: Ethernet1/1
      switches:
      - 192.168.1.224
    - name: SN-12
      type: firewall
      form_factor: virtual
      svc_int_name: svc1
      attach_interface: vPC1
      switches:  # up to two switches, if two switches are provided, vpc is only option
      - 192.168.1.224
      - 192.168.1.225

- name: Query all the Service Nodes
  cisco.dcnm.dcnm_service_node:
    fabric: Fabric1
    service_fabric: external
    state: query
```
