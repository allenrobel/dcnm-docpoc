# dcnm_service_policy

???+ "Details"

    - short_description
        - DCNM ansible module for managing service policies.
    - version_added
        - 1.2.0
    - description
        - DCNM ansible module for creating, deleting, querying and modifying service policies
    - author
        - Mallik Mudigonda (@mmudigon)


## options

???+ "Details"


### fabric

???+ "Details"

    - description
        - 'name of the target fabric for service policy operations'
    - type
        - str
    - required
        - True

### service_fabric

???+ "Details"

    - description
        - 'name of the external fabric attached to the service node for service policy operations'
    - type
        - str
    - required
        - True

### state

???+ "Details"

    - description
        - the required state of the configuration after module completion.
    - type
        - str
    - required
        - False
    - choices
        - merged
        - replaced
        - overridden
        - deleted
        - query
    - default
        - merged

### attach

???+ "Details"

    - description
        - a flag specifying if the given service policy is to be attached to the specified service node
    - type
        - bool
    - required
        - False
    - default
        - True

### deploy

???+ "Details"

    - description
        - a flag specifying if a service policy is to be deployed on the switches
    - type
        - bool
    - required
        - False
    - default
        - True

### config

???+ "Details"

    - description
        - a list of dictionaries containing service policy and switch information
    - type
        - list
    - elements
        - dict

#### name

???+ "Details"

    - description
        - a unique name which identifies the service policy
    - type
        - str
    - required
        - True

#### src_vrf

???+ "Details"

    - description
        - name of the source vrf for this service policy
    - type
        - str
    - required
        - True

#### dest_vrf

???+ "Details"

    - description
        - name of the destination vrf for this service policy
    - type
        - str
    - required
        - True

#### src_network

???+ "Details"

    - description
        - name of the source network for this service policy
    - type
        - str
    - required
        - True

#### dest_network

???+ "Details"

    - description
        - name of the destination network for this service policy
    - type
        - str
    - required
        - True

#### next_hop

???+ "Details"

    - description
        - next hop ip address to be used in source to network direction 
        - This must exactly match the next hop IP configured for the route peering associated with this policy
    - type
        - str
    - required
        - False
    - default
        - 

#### reverse_next_hop

???+ "Details"

    - description
        - reverse next hop ip address to be used in network to source direction 
        - This must exactly match the reverse next hop IP configured for the route peering associated with this policy
    - type
        - str
    - required
        - False
    - default
        - 

#### policy

???+ "Details"

    - description
        - details of the policy (ACL) to be applied
    - type
        - dict

##### proto

???+ "Details"

    - description
        - protocol to be matched to apply this ACL
    - type
        - str
    - required
        - True
    - choices
        - ip
        - icmp
        - tcp
        - udp

##### src_port

???+ "Details"

    - description
        - source port number to be matched to apply this ACL
    - type
        - str
    - required
        - True
    - choices
        - any
        - Min 1
        - Max 65535

##### dest_port

???+ "Details"

    - description
        - destination port number to be matched to apply this ACL
    - type
        - str
    - required
        - True
    - choices
        - any
        - Min 1
        - Max 65535

##### action

???+ "Details"

    - description
        - action to apply for traffic matching the service profile
    - type
        - str
    - required
        - False
    - choices
        - permit
        - deny
    - default
        - permit

##### next_hop_option

???+ "Details"

    - description
        - option to specify how to redirect traffic
    - type
        - str
    - required
        - False
    - choices
        - none
        - drop-on-fail
        - drop
    - default
        - none

##### acl_name

???+ "Details"

    - description
        - Name of the ACL in the forward direction
    - type
        - str
    - required
        - False
    - default
        - will be auto-generated by DCNM

##### rev_acl_name

???+ "Details"

    - description
        - Name of the ACL in the reverse direction
    - type
        - str
    - required
        - False
    - default
        - will be auto-generated by DCNM

##### route_map_num

???+ "Details"

    - description
        - route map match number 
        - Minimum Value (1), Maximum Value (65535) 
        - Default value is auto-generated by DCNM
    - type
        - int
    - required
        - False

##### rev_route_map_num

???+ "Details"

    - description
        - route map match number for reverse direction 
        - Minimum Value (1), Maximum Value (65535) 
        - Default value is auto-generated by DCNM
    - type
        - int
    - required
        - False