## Bit Zesty's Ansible Packages Role

**For recent changes please refer to [the changelog](https://github.com/bitzesty/ansible_deployer/blob/master/CHANGELOG.md)**.

Sets up deployer user account.

* Creates new deployer user
* Sets up SSH Authorized Keys
* Uploads deployer's SSH Private Key
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

Deployer keyscan domains (adds Domain to known hosts):
```
deployer_ssh_keyscan_domains:
  - github.com
```

Deployer authorized keys (list of authorized SSH keys).
They would be added to /home/{{ deployer }}/.ssh/authorized_keys.
```
deployer_authorized_keys: [
  "ssh-rsa AAAAB3NzaC1yc2EAAA ....",
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
