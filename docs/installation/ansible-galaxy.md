# ansible-galaxy

## Installing the latest version

You can install the Cisco DCNM collection with the Ansible Galaxy CLI.

``` bash title="Installing with ansible-galaxy"
ansible-galaxy collection install cisco.dcnm
```

## Installing a specific version

To install a specific version, you can include it in
a `requirements.yml` file and install with the following.

``` bash title="Installing a specific version"
ansible-galaxy collection install -r requirements.yml
```

Where `requirements.yml` contains.

``` yaml title="requirements.yml"
---
collections:
  - name: cisco.dcnm
    version: 3.5.1
```
