Nutanix Role for Prism API Initialization
=========

This Ansible role takes input variable for a Prism IP (PE or PC), a username and a password and generates facts that can be used to make API calls as necessary. This role is used as a basis for other roles to interact with the Nutanix API.


Role Variables
--------------

Inputs

| Variable                 | Required | Default | Choices                   | Comments                                                                             |
|--------------------------|----------|---------|---------------------------|--------------------------------------------------------------------------------------|
| nutanix_host             | yes      |         |                           | The IP address or FQDN for the Prism (Element or Central) which you want to connect. |
| prism_username           | yes      |         |                           | A valid username with appropriate rights to access the Nutanix API.                  |
| prism_password           | yes      |         |                           | A valid password for the supplied username.                                          |
| prism_port               | no       | 9440    |                           | The Prism TCP port.                                                                  |
| validate_certs           | no       | no      | yes | no                  | Whether to check if Prism UI certificates are valid.                                 |


Outputs

| Variable                 | Required | Default | Choices                   | Comments                                                                    |
|--------------------------|----------|---------|---------------------------|-----------------------------------------------------------------------------|
| prism_api_auth           |          |         |                           | Base64 encoded string for be used for basic authentication                  |
| prism_api_v1             |          |         |                           | Set to https://[prism_ip]:[prism_port]/PrismGateway/services/rest/v1        |
| prism_api_v2             |          |         |                           | Set to https://[prism_ip]:[prism_port]/PrismGateway/services/rest/v2.0      |
| prism_api_v3             |          |         |                           | Set to https://[prism_ip]:[prism_port]/api/nutanix/v3                       |
| prism_api_lcm            |          |         |                           | Set to https://[prism_ip]:[prism_port]/lcm/v1.r0.b1                         |
| prism_api_v4_clustermgmt |          |         |                           | Set to https://[prism_ip]:[prism_port]/api/clustermgmt/v4.0.a1              |
| prism_api_v4_prism       |          |         |                           | Set to https://[prism_ip]:[prism_port]/api/prism/v4.0.a1                    |
| prism_api_v4_storage     |          |         |                           | Set to https://[prism_ip]:[prism_port]/api/storage/v4.0.a2                  |
| prism_api_v4_vmm         |          |         |                           | Set to https://[prism_ip]:[prism_port]/api/vmm/v4.0.a1                      |


Dependencies
------------

None.

Example Playbook
----------------

This example will build all necessary facts for future roles consuming the Nutanix REST APIs.

```
- hosts: prism_element
  gather_facts: false
  roles:
    - nutanix-ansible-galaxy-role-init-api
  vars:
    nutanix_host: 10.38.185.37
    nutanix_username: admin
    nutanix_password: nx2Tech165!
```

License
-------

See LICENSE.md

Author Information
------------------

Ross Davies
