## Bit Zesty's Ansible Deployer Role

**For recent changes please refer to [the changelog](https://github.com/bitzesty/ansible_deployer/blob/master/CHANGELOG.md)**.

Sets up deployer user account.

* Applies custom SSH config files (/etc/ssh/ssh_config and /etc/ssh/sshd_config)
* Creates new deployer user
* Uploads deployer's SSH Private Key
* Uploads SSH Authorized Keys
* Uploads SSH keys from github.com for list of trusted users
* Add Specific Domain SSH Keys (github.com) to known hosts
* Adds custom .bashrc, .profile, .gemrc, .bundle files for deployer user

#### Role Variables

Deployer user (default is 'deployer'):
```
user: "johnconnor"
```

Home directory (default is '/home/{{ user }}'):
```
home_directory: "/home/vasily"
```

Trusted domains (defailt: ['github']).
Adds trusted domains to known hosts.
```
deployer_ssh_keyscan_domains:
  - bitbucket.org
```

Trusted authorized SSH keys (defailt: []).
Uploads authorized SSH keys to /home/{{ deployer }}/.ssh/authorized_keys.
```
deployer_authorized_keys: [
  "ssh-rsa AAAAB3NzaC1yc2EAAA ....",
  ...
]
```

List of trusted usernames from github.com (defailt: []).
Uploads SSH keys from github.com for trusted github usernames.
```
trusted_usernames_from_github: [
  "ryanb",
  "dhh",
  ...
]
```

#### Role Templates

```
bashrc-user
gemrc
profile
ssh_config
sshd_config
```

#### Example Playbook

```
- hosts: ci-server
  vars:
    user: "johnconnor"
    deployer_ssh_keyscan_domains:
      - bitbucket.org
      - github.com
    deployer_authorized_keys: [
      "ssh-rsa AAAAB3NzaC1yc2EAAA ....",
      ...
    ]
    trusted_usernames_from_github: [
      "ryanb",
      "dhh",
      ...
    ]
  roles:
    - { role: bitzesty.deployer }
```

#### License

MIT / BSD

#### Author Information

This role was created in 2015 by developers from [Bitzesty LTD](https://github.com/bitzesty).
