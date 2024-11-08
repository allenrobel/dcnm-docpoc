# [dcnm.py]

[dcnm.py]: https://github.com/CiscoDevNet/ansible-dcnm/blob/develop/plugins/httpapi/dcnm.py

## author

Mike Wiebe (@mikewiebe)

## name

dcnm

## short_description

Ansible DCNM HTTPAPI Plugin.

## description

This DCNM plugin provides the HTTPAPI transport methods needed to initiate
a connection to the DCNM controller, send API requests and process the
respsonse from the controller.

## version_added

`0.9.0`

## options

### login_domain

#### description

The login domain name to use for user authentication

Only needed for NDFC

#### type

string

#### default

local

#### env

##### name

`ANSIBLE_HTTPAPI_LOGIN_DOMAIN`

#### vars

##### name

`ansible_httpapi_login_domain`
