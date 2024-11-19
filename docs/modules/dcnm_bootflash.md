# dcnm_bootflash

???+ "Details"

    - author
        - Allen Robel (@quantumonion)
    - description
        - Delete, query bootflash files.
    - short_description
        - Bootflash management for Nexus switches.
    - version_added
        - 3.6.0


## options

???+ "Details"


### config

???+ "Details"

    - description
        - Configuration parameters for the module.
    - required
        - True

#### switches

???+ "Details"

    - description
        - List of dictionaries containing switches on which query or delete operations are executed.
    - elements
        - dict

##### ip_address

???+ "Details"

    - description
        - The ip address of a switch.
    - required
        - True
    - type
        - str

##### targets

???+ "Details"

    - default
        - []
    - description
        - List of dictionaries containing options for files to be deleted or queried.
    - elements
        - dict
    - required
        - False

###### filepath

???+ "Details"

    - description
        - The path to the file to be deleted or queried.  Only files in the root directory of the partition are currently supported.
    - required
        - True
    - type
        - str

###### supervisor

???+ "Details"

    - choices
        - active
        - standby
    - default
        - active
    - description
        - Either active or standby. The supervisor containing the filepath.
    - required
        - False
    - type
        - str
    - type
        - list
    - type
        - list

#### targets

???+ "Details"

    - default
        - []
    - description
        - List of dictionaries containing options for files to be deleted or queried.
    - elements
        - dict
    - required
        - False

##### filepath

???+ "Details"

    - description
        - The path to the file to be deleted or queried.
    - required
        - True
    - type
        - str

##### supervisor

???+ "Details"

    - choices
        - active
        - standby
    - default
        - active
    - description
        - Either active or standby. The supervisor containing the filepath.
    - required
        - False
    - type
        - str
    - type
        - list
    - type
        - dict

### state

???+ "Details"

    - choices
        - deleted
        - query
    - default
        - query
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
#   Delete files from the bootflash of one or more switches.
#
#   If an image is in use by a device, the module will fail.  Use
#   dcnm_image_upgrade module, state deleted, to detach image policies
#   containing images to be deleted.
#
# query:
#
#   Return information for one or more files.
#
# Delete two files from each of three switches.

- name: Delete two files from each of two switches
  cisco.dcnm.dcnm_bootflash:
    state: deleted
    config:
      targets:
        - filepath: bootflash:/foo.txt
          supervisor: active
        - filepath: bootflash:/bar.txt
          supervisor: standby
      switches:
        - ip_address: 192.168.1.1
        - ip_address: 192.168.1.2
        - ip_address: 192.168.1.3

# Delete two files from switch 192.168.1.1 and switch 192.168.1.2:
#   - foo.txt on the active supervisor's bootflash: device.
#   - bar.txt on the standby supervisor's bootflash: device.
# Delete potentially multiple files from switch 192.168.1.3:
#   - All txt files on the standby supervisor's bootflash: device
#     that match the pattern 202401??.txt, e.g. 20240123.txt.
# Delete potentially multiple files from switch 192.168.1.4:
#   - All txt files on all flash devices on active supervisor.

- name: Delete files
  cisco.dcnm.dcnm_bootflash:
    state: deleted
    config:
      targets:
        - filepath: bootflash:/foo.txt
          supervisor: active
        - filepath: bootflash:/bar.txt
          supervisor: standby
      switches:
        - ip_address: 192.168.1.1
        - ip_address: 192.168.1.2
        - ip_address: 192.168.1.3
          targets:
            - filepath: bootflash:/202401??.txt
              supervisor: standby
        - ip_address: 192.168.1.4
          targets:
            - filepath: "*:/*.txt"
              supervisor: active
  register: result
- name: print result
  ansible.builtin.debug:
    var: result

# Query the controller for information about one file on three switches.
# Since the default for supervisor is "active", the module will query the
# active supervisor's bootflash: device.

- name: Query file on three switches
  cisco.dcnm.dcnm_bootflash:
    state: query
    config:
      targets:
        - filepath: bootflash:/foo.txt
    switches:
      - ip_address: 192.168.1.1
      - ip_address: 192.168.1.2
      - ip_address: 192.168.1.3
  register: result
- name: print result
  ansible.builtin.debug:
    var: result

```
