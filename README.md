# Ansible role `389ds`

An Ansible role for installing and configuring a 389 directory server. Specifically, the responsibilities of this role are to:

- Install a 389 Directory Server on RedHat systems
- Configure LDAP users and OU's in a comprehensive way (To be added)

## Requirements

No specific requirements

## Role Variables

| Variable                | Purpose                                                                                   |
| :-------                | :------                                                                                   |
| `dirsrv_password`       | Password, **be sure to set**                                                              |
| `dirsrv_admin_password` | Admin password ( Default: dirsrv_password )                                               |
| `dirsrv_fqdn`           | FQDN  (Default: ansible_fqdn, if ansible_fqdn fails or is wrong for you, set proper one ) |
| `dirsrv_suffix`         | Default: last two parts from dirsrv_fqdn                                                  |
| `dirsrv_hostname`       | Default: first part from dirsrv_fqdn                                                      |
| `dirsrv_ip`             | IP address of the 389 directory server. Default `127.0.0.1`                               |
| `dirsrv_remove_entries` | List of default LDAP entries to be deleted when installing                                |
| `dirsrv_groups`         | List of groups to be created on directory server                                          |
| `dirsrv_users`          | List of users to be created on directory server                                           |

## Dependencies
- `bertvv.rh-base` role to add and open the required ports

## Prerequisites
- Open the required ports for LDAP:
```yml
rhbase_firewall_allow_ports:
  - 389/tcp
  - 9830/tcp
  - 636/tcp
  - 3269/tcp
```

## Example Playbook
### Remove entries
```yaml
dirsrv_remove_entries:
  - "ou=Special Users,dc=green,dc=local"
  - "cn=Accounting Managers,ou=Groups,dc=green,dc=local"
```

### Add groups
```yaml
dirsrv_groups:
  - name: it
    gidnumber: 1001
    members:
      - linus
  - name: sales
    gidnumber: 1002
    members:
      - mark
```

### Add users
```yml
dirsrv_users:
  - uid: linus
    cn: Linus
    sn: Torvalds
    description: Linus Torvalds
    password: "{SSHA}dIfwvAy7VNBkjywXaAXsgLPCiXemGegCShfPVQ==" # hash for "Test123"
    uidnumber: 700
    gidnumber: 700
    loginshell: /bin/bash
    homedirectory: /home/linus
```



## Contributing

Issues, feature requests, ideas are appreciated and can be posted in the Issues section.

Pull requests are also very welcome. The best way to submit a PR is by first creating a fork of this Github project, then creating a topic branch for the suggested change and pushing that branch to your own fork. Github can then easily create a PR based on that branch. Don't forget to add your name to the contributor list below!

## License

3-clause BSD license, see [LICENSE](LICENSE.md)

## Thank word
Role is based on an outdated role created by [sasilen](https://github.com/sasilen). 

## Contributors

- [Bert Van Vreckem](https://github.com/bertvv/) (maintainer of role skeleton)
- [Lennert Mertens](https://github.com/LennertMertens)
- [Ismail El Kaddourri](https://github.com/ismailelk)
