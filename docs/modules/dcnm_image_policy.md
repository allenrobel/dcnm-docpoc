# dcnm_image_policy

???+ "Details"

    - author
        - Allen Robel (@quantumonion)
    - description
        - Create, delete, modify image policies.
    - short_description
        - Image policy management for Nexus Dashboard Fabric Controller
    - version_added
        - 3.5.0


## options

???+ "Details"


### config

???+ "Details"

    - default
        - []
    - description
        - List of dictionaries containing image policy parameters
    - elements
        - dict

#### agnostic

???+ "Details"

    - default
        - False
    - description
        - The agnostic flag.
    - required
        - False
    - type
        - bool

#### description

???+ "Details"

    - default
        - 
    - description
        - The image policy description.
    - required
        - False
    - type
        - str

#### epld_image

???+ "Details"

    - default
        - 
    - description
        - The epld image name.
    - required
        - False
    - type
        - str

#### name

???+ "Details"

    - description
        - The image policy name.
    - required
        - True
    - type
        - str

#### packages

???+ "Details"

    - description
        - A dictionary containing two keys, install and uninstall.
    - required
        - False

##### install

???+ "Details"

    - description
        - A list of packages to install.
    - elements
        - str
    - required
        - False
    - type
        - list

##### uninstall

???+ "Details"

    - description
        - A list of packages to uninstall.
    - elements
        - str
    - required
        - False
    - type
        - list
    - type
        - dict

#### platform

???+ "Details"

    - description
        - The platform to which the image policy applies e.g. N9K.
    - required
        - True
    - type
        - str

#### release

???+ "Details"

    - description
        - The release associated with the image policy. 
        - This is derived from the image name as follows. 
        - From image name nxos64-cs.10.2.5.M.bin 
        - we need to extract version (10.2.5), platform (nxos64-cs), and bits (64bit). 
        - The release string conforms to format (version)_(platform)_(bits) 
        - so the resulting release string will be 10.2.5_nxos64-cs_64bit
    - required
        - True
    - type
        - str

#### type

???+ "Details"

    - default
        - PLATFORM
    - description
        - The type of the image policy e.g. PLATFORM.
    - required
        - False
    - type
        - str
    - type
        - list

### state

???+ "Details"

    - choices
        - deleted
        - merged
        - overridden
        - query
        - replaced
    - default
        - merged
    - description
        - The state of the feature or object after module completion
    - type
        - str

## Examples

???+ "Details"

``` yaml
---
# This module supports the following states:
#
# deleted:
#   Delete image policies from the controller.
#
#   If an image policy has references (i.e. it is attached to a device),
#   the module will fail.  Use dcnm_image_upgrade module, state deleted,
#    to detach the image policy from all devices before deleting it.
#
# merged:
#   Create (or update) one or more image policies.
#
#   If an image policy does not exist on the controller, create it.
#   If an image policy already exists on the controller, edit it.
#
# overridden:
#   Create/delete one or more image policies.
#
#   If an image policy already exists on the controller, delete it and update
#   it with the configuration in the playbook task.
#
#   Remove any image policies from the controller that are not in the
#   playbook task.
#
# query:
#
#   Return the configuration for one or more image policies.
#
# replaced:
#
#   Replace image policies on the controller with policies in the playbook task.
#
#   If an image policy exists on the controller, but not in the playbook task,
#   do not delete it or modify it.
#
# Delete two image policies from the controller.

    -   name: Delete Image policies
        cisco.dcnm.dcnm_image_policy:
            state: deleted
            config:
            -   name: KR5M
            -   name: NR3F
        register: result
    -   name: print result
        ansible.builtin.debug:
            var: result

# Merge two image policies into the controller.

    -   name: Merge Image policies
        cisco.dcnm.dcnm_image_policy:
            state: merged
            config:
            -   name: KR5M
                agnostic: false
                description: KR5M
                epld_image: n9000-epld.10.2.5.M.img
                packages:
                   install:
                   - mtx-openconfig-all-2.0.0.0-10.4.1.src.rpm
                   uninstall:
                   - mtx-grpctunnel-2.1.0.0-10.4.1.lib32_64_n9000
                platform: N9K
                release: 10.2.5_nxos64-cs_64bit
                type: PLATFORM
            -   name: NR3F
                description: NR3F
                platform: N9K
                epld_image: n9000-epld.10.3.1.F.img
                release: 10.3.1_nxos64-cs_64bit
        register: result
    -   name: print result
        ansible.builtin.debug:
            var: result

# Override all policies on the controller and replace them with
# the policies in the playbook task.  Any policies other than
# KR5M and NR3F are deleted from the controller.

    -   name: Override Image policies
        cisco.dcnm.dcnm_image_policy:
            state: overridden
            config:
            -   name: KR5M
                agnostic: false
                description: KR5M
                epld_image: n9000-epld.10.2.5.M.img
                platform: N9K
                release: 10.2.5_nxos64-cs_64bit
                type: PLATFORM
            -   name: NR3F
                description: NR3F
                platform: N9K
                epld_image: n9000-epld.10.2.5.M.img
                release: 10.3.1_nxos64-cs_64bit
        register: result
    -   name: print result
        ansible.builtin.debug:
            var: result

# Query the controller for the policies in the playbook task.

    -   name: Query Image policies
        cisco.dcnm.dcnm_image_policy:
            state: query
            config:
            -   name: NR3F
            -   name: KR5M
        register: result
    -   name: print result
        ansible.builtin.debug:
            var: result

# Replace any policies on the controller that are in the playbook task with
# the configuration given in the playbook task.  Policies not listed in the
# playbook task are not modified and are not deleted.

    -   name: Replace Image policies
        cisco.dcnm.dcnm_image_policy:
            state: replaced
            config:
            -   name: KR5M
                agnostic: false
                description: KR5M
                epld_image: n9000-epld.10.2.5.M.img
                platform: N9K
                release: 10.2.5_nxos64-cs_64bit
                type: PLATFORM
            -   name: NR3F
                description: Replaced NR3F
                platform: N9K
                epld_image: n9000-epld.10.3.1.F.img
                release: 10.3.1_nxos64-cs_64bit
        register: result
    -   name: print result
        ansible.builtin.debug:
            var: result
```
