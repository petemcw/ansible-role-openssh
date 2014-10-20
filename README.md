# OpenSSH Role for Ansible

This role configures the portable version of OpenSSH, a free implementation of
the Secure Shell protocol.

## Requirements

This role requires [Ansible](http://www.ansibleworks.com/) version 1.4 or higher
and the Debian/Ubuntu platform.

## Role Variables

The variables that can be passed to this role and a brief description about
them are as follows (additional variables are available in the source):

```yaml
# The default SSH port
openssh_port: 22

# If set, the list of user accounts allowed to access the server via SSH
openssh_allow_users:
  - 'deploy_user'

# If set, the list of groups allowed to access the server via SSH
openssh_allow_groups:
  - 'admin'

# If set, the list of user accounts that will be specifically allowed password
# authentication regardless of the global setting
openssh_password_auth_users:
  - 'password_user'

# The default flag for whether to allow the root user login privileges
openssh_permit_root_login: false

# The default flag for whether to enable public key authentication
openssh_use_publickey_auth: true

# The default flag for whether to enable password-based authentication
openssh_use_password_auth: false
```

## Examples

1. Install OpenSSH with default settings

    ```yaml
    ---
    # This playbook installs OpenSSH

    - name: Apply OpenSSH to all nodes
      hosts: all
      roles:
        - openssh
    ```

2. Install OpenSSH with customized SSH configuration

    ```yaml
    ---
    # This playbook installs OpenSSH

    - name: Apply OpenSSH to all nodes
      hosts: all
      roles:
        - { role: openssh,
            openssh_port: 2222,
            openssh_use_publickey_auth: true,
            openssh_use_password_auth: false,
            openssh_allow_users: ['deploy_user']
          }
    ```

## Dependencies

None.

## License

MIT.
