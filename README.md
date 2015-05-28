## Bit Zesty's Ansible Packages Role

**For recent changes please refer to [the changelog](https://github.com/bitzesty/ansible_deployer/blob/master/CHANGELOG.md)**.

Sets up deployer user account.

* Creates new deployer user
* Uploads deployer's SSH Private Key
* Uploads SSH Authorized Keys
* Uploads SSH keys from github.com for list of trusted users
* Add Specific Domains SSH Keys (github.com) to known hosts
* Adds default deployer's .bashrc, .profile, .gemrc, .bundle

#### Role Variables

Deployer user (default is 'deployer'):
```
user: "johnconnor"
```

Home directory (default is '/home/{{ user }}')
```
home_directory: "/home/vasily"
```

Adds trusted domains to known hosts (default is 'github.com' only):
```
deployer_ssh_keyscan_domains:
  - bitbucket.org
```

Deployer authorized keys (list of authorized SSH keys).
They would be added to /home/{{ deployer }}/.ssh/authorized_keys.
```
deployer_authorized_keys: [
  "ssh-rsa AAAAB3NzaC1yc2EAAA ....",
  ...
]
```

List of trusted usernames from github.com:
```
trusted_usernames_from_github: [
  "ryanb",
  "dhh",
  ...
]
```

#### Example Playbook

```
- hosts: ci-server
  vars:

  roles:
    - { role: bitzesty.packages }
```

#### License

MIT / BSD

#### Author Information

This role was created in 2015 by developers from [Bitzesty LTD](https://github.com/bitzesty).
