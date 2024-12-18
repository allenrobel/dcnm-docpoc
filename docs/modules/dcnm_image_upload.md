# dcnm_image_upload

???+ "Details"

    - author
        - Mallik Mudigonda(@mmudigon)
    - description
        - DCNM Ansible Module for the following image management operations 
        - Upload, Delete, and Display NXOS images from the controller
    - short_description
        - DCNM Ansible Module for managing images.
    - version_added
        - 3.5.0


## options

???+ "Details"


### files

???+ "Details"

    - default
        - []
    - description
        - A dictionary of images and other related information that is required to download the same.
    - elements
        - dict

#### password

???+ "Details"

    - description
        - Password to be used to log into the image hosting server. This parameter is required only if source is 'scp' 
        - or 'sftp'.
    - required
        - True
    - type
        - str

#### path

???+ "Details"

    - description
        - Full path to the image that is being uploaded to the controller. For deleting an image 
        - the exact image name must be provided.
    - required
        - True
    - type
        - str

#### remote_server

???+ "Details"

    - description
        - IP address of the server hosting the image. This parameter is required only if source is 'scp' 
        - or 'sftp'.
    - required
        - True
    - type
        - str

#### source

???+ "Details"

    - choices
        - scp
        - sftp
        - local
    - default
        - local
    - description
        - Protocol to be used to download the image from the controller.
    - type
        - str

#### user_name

???+ "Details"

    - description
        - User name to be used to log into the image hosting server. This parameter is required only if source is 'scp' 
        - or 'sftp'.
    - required
        - True
    - type
        - str
    - type
        - list

### state

???+ "Details"

    - choices
        - merged
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
#   Images defined in the playbook will be merged into the controller.
#
#   The images listed in the playbook will be created if not already present on the server
#   server. If the image is already present and the configuration information included
#   in the playbook is either different or not present in server, then the corresponding
#   information is added to the server. If an image mentioned in playbook
#   is already present on the server and there is no difference in configuration, no operation
#   will be performed for such interface.
#
# Overridden:
#   Images defined in the playbook will be overridden in the controller.
#
#   The state of the images listed in the playbook will serve as source of truth for all
#   the images on the controller. Additions and deletions will be done to bring
#   the images on the controller to the state listed in the playbook. All images other than the
#   ones mentioned in the playbook will be deleted.
#   Note: Override will work on the all the images present in the controller.
#
# Deleted:
#   Images defined in the playbook will be deleted from the controller.
#
#   Deletes the list of images specified in the playbook. If the playbook does not include
#   any image information, then all images from the controller will be deleted.
#
# Query:
#   Returns the current state for the images listed in the playbook.

# UPLOAD IMAGES

- name: Upload images to controller
  cisco.dcnm.dcnm_image_upload: &img_upload
    state: merged                             # choose form [merged, deleted, overridden, query], default is merged
    files:
      - path: "full/path/to/image1"           # Full path to the image on the server
        source: scp                           # choose from [local, scp, sftp], default is local
        remote_server: "192.168.1.1"          # mandatory when the source is scp or sftp
        username: "image_upload"              # mandatory when source is scp or sftp
        password: "image_upload"              # mandatory when source is scp or sftp

      - path: "full/path/to/image2"           # Full path to image on local host
        source: local                         # choose from [local, scp, sftp], default is local

      - path: "full/path/to/image3"           # Full path to the image on the server
        source: sftp                          # choose from [local, scp, sftp], default is local
        remote_server: "192.168.1.1"          # mandatory when the source is scp or sftp
        username: "image_upload"              # mandatory when source is scp or sftp
        password: "image_upload"              # mandatory when source is scp or sftp

# DELETE IMAGES

- name: Delete an image
  cisco.dcnm.dcnm_image_upload:
    state: deleted                            # choose form [merged, deleted, overridden, query], default is merged
    files:
      - name: "nxos.9.3.8.bin"                # Name of the image on the controller

- name: Delete an image - without explicitly including any config
  cisco.dcnm.dcnm_image_upload:
    state: deleted                            # choose form [merged, deleted, overridden, query], default is merged

# OVERRIDE IMAGES

- name: Override without any config
  cisco.dcnm.dcnm_image_upload:
    state: overridden                         # choose form [merged, deleted, overridden, query], default is merged

- name: Override with a new config
  cisco.dcnm.dcnm_image_upload: &image_override
    state: overridden                         # choose form [merged, deleted, overridden, query], default is merged
    files:
      - path: "full/path/to/image4"           # Full path to the image on local server
        source: local                         # choose from [local, scp, sftp], default is local

# QUERY IMAGES

- name: Query for existing image
  cisco.dcnm.dcnm_image_upload:
    state: query                              # choose form [merged, deleted, overridden, query], default is merged
    files:
      - name: "nxos.9.3.8.bin"                # Name of the image to be used to filter the output

- name: Query without any filters
  cisco.dcnm.dcnm_image_upload:
    state: query                              # choose form [merged, deleted, overridden, query], default is merged
```
