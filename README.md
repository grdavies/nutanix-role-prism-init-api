Nutanix Role for Prism API Initialization
=========

This Ansible role takes input variable for a Prism IP (PE or PC), a username and a password and generates facts that can be used to make API calls as necessary. This role is used as a basis for other roles to interact with the Nutanix API.


Role Variables
--------------

| Variable                | Required | Default | Choices                   | Comments                                                                    |
|-------------------------|----------|---------|---------------------------|-----------------------------------------------------------------------------|
| prism_ip                | yes      |         |                           | The IP address of the Prism (Element or Central) which you want to connect. |
| prism_username          | yes      |         |                           | A valid username with appropriate rights to access the Nutanix API.         |
| prism_password          | yes      |         |                           | A valid password for the supplied username.                                 |
| port                    | no       | 9440    |                           | The Prism TCP port.                                                         |
| validate_certs          | no       | no      | yes | no                  | Whether to check if Prism UI certificates are valid.                        |


Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: prism_element
      gather_facts: false
      roles:
        - nutanix-ansible-galaxy-role-init-api
      vars:
        prism_ip: 10.38.185.37
        prism_username: admin
        prism_password: nx2Tech165!


License
-------

See LICENSE.md

Author Information
------------------

Ross Davies
