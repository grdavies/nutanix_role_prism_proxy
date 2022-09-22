# Nutanix Role for Prism HTTP proxy server configuration

This Ansible role sets the HTTP proxy configuration for Prism Element and Prism Central.


## Role Variables

| Variable                 | Required | Default  | Choices                                                                         | Comments                                                                                                                                           |
|--------------------------|----------|----------|---------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| validate_certs           | no       | no       |                                                                                 | Whether to check if Prism UI certificates are valid.                                                                                               |
| prism_proxy_name         | yes      |          |                                                                                 | Name for the proxy server in the Prism UI                                                                                                          |
| prism_proxy_address      | yes      |          |                                                                                 | FQDN or IP address for the proxy server                                                                                                            |
| prism_proxy_port         | yes      |          |                                                                                 | TCP port for the proxy server                                                                                                                      |
| prism_proxy_types        | no       | ['http'] | ['http', 'https']                                                               | Whether to proxy http traffic, https traffic or both                                                                                               |
| prism_proxy_username     | no       |          |                                                                                 | Username to authenticate to the proxy server                                                                                                       |
| prism_proxy_password     | no       |          |                                                                                 | Password for username to authenticate to the proxy server                                                                                          |
| prism_proxy_whitelist    | no       | []       |                                                                                 | List of FQDNs or IP addresses to be added to the proxy whitelist                                                                                   |


## Dependencies

- grdavies.nutanix_role_prism_init_api


## Example Playbook

```
- hosts: localhost
  gather_facts: false
  roles:
    - role: grdavies.nutanix_role_prism_proxy
  vars:
    prism_ip: 10.38.185.37
    prism_username: admin
    prism_password: nx2Tech165!
    prism_proxy_name: my_proxy
    prism_proxy_address: proxy.ntnxlab.local
    prism_proxy_port: 8080
    prism_proxy_types:
      - http
      - https
    prism_proxy_whitelist:
      - "*.ntnxlab.local"
```


## License

See LICENSE.md

## Author Information

Ross Davies
