# dcnm_template

???+ "Details"

    - author
        - Mallik Mudigonda(@mmudigon)
    - description
        - DCNM Ansible Module for creating, deleting and modifying template service 
        - operations
    - short_description
        - DCNM Ansible Module for managing templates.
    - version_added
        - 1.1.0


## options

???+ "Details"


### config

???+ "Details"

    - description
        - A dictionary of template operations
    - elements
        - dict
    - required
        - True

#### content

???+ "Details"

    - description
        - Multiple line configuration snip that can be used to associate to devices as policy
    - type
        - str

#### description

???+ "Details"

    - default
        - 
    - description
        - Description of the template. The description may include the details regarding the content
    - type
        - str

#### name

???+ "Details"

    - description
        - Name of the template.
    - type
        - str

#### tags

???+ "Details"

    - default
        - 
    - description
        - User defined labels for identifying the templates
    - type
        - str

#### type

???+ "Details"

    - choices
        - cli
        - python
    - default
        - cli
    - description
        - Type of the template content either CLI or Python
    - type
        - str
    - type
        - list

### state

???+ "Details"

    - choices
        - merged
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
#   Templates defined in the playbook will be merged into the target.
#
#   The templates listed in the playbook will be created if not already present on the DCNM
#   server. If the template is already present and the configuration information included
#   in the playbook is either different or not present in DCNM, then the corresponding
#   information is added to the template on DCNM. If a template mentioned in playbook
#   is already present on DCNM and there is no difference in configuration, no operation
#   will be performed for such a template.
#
# Deleted:
#   Templates defined in the playbook will be deleted from the target.
#
#   Deletes the list of templates specified in the playbook.
#
# Query:
#   Returns the current DCNM state for the templates listed in the playbook.


# To create or modify templates

- name: Create or modify templates
  cisco.dcnm.dcnm_template:
    state: merged        # only choose form [merged, deleted, query]
    config:
      - name: template_101
        description: "Template_101"
        tags: "internal policy 101"
        content: |
          telemetry
            certificate /bootflash/telegraf.crt telegraf
            destination-profile
              use-vrf management
            destination-group 101
              ip address 10.195.225.176 port 57101 protocol gRPC encoding GPB
            sensor-group 101
              data-source DME
              path sys/ch depth unbounded
            subscription 101
              dst-grp 101
              snsr-grp 101 sample-interval 10101

      - name: template_102
        description: "Template_102"
        tags: "internal policy 102"
        content: |
          telemetry
            certificate /bootflash/telegraf.crt telegraf
            destination-profile
              use-vrf management
            destination-group 1
              ip address 10.195.225.102 port 57102 protocol gRPC encoding GPB
            sensor-group 102
              data-source DME
              path sys/ch depth unbounded
            subscription 102
              dst-grp 102
              snsr-grp 102 sample-interval 10102

# To delete templates

- name: Delete templates
  cisco.dcnm.dcnm_template:
    state: deleted       # only choose form [merged, deleted, query]
    config:
      - name: template_101

      - name: template_102

      - name: template_103

      - name: template_104

# To query templates

- name: Query templates
  cisco.dcnm.dcnm_template:
    state: query       # only choose form [merged, deleted, query]
    config:
      - name: template_101

      - name: template_102

      - name: template_103

      - name: template_104
```
