# Ansible role `389ds`

An Ansible role for installing and configuring a 389 directory server. Specifically, the responsibilities of this role are to:

- Install a 389 Directory Server on RedHat systems
- Configure LDAP users and OU's in a comprehensive way (To be added)

## Requirements

No specific requirements

## Role Variables


| Variable | Purpose |
| :------- | :------ |
| `dirsrv_password` | Password, **be sure to set** |
| `dirsrv_admin_password` | Admin password ( Default: dirsrv_password ) |
| `dirsrv_fqdn` | FQDN  (Default: ansible_fqdn, if ansible_fqdn fails or is wrong for you, set proper one )|
| `dirsrv_suffix` | Default: last two parts from dirsrv_fqdn |
| `dirsrv_hostname` | Default: first part from dirsrv_fqdn |
| `dirsrv_ip` | IP address of the 389 directory server. Default `127.0.0.1`|

## Dependencies
- `bertvv.rh-base` role to add and open the required ports

## Example Playbook

See the test playbooks in either the [Vagrant](https://github.com/bertvv/ansible-role-ROLENAME/blob/vagrant-tests/test.yml) or [Docker](https://github.com/bertvv/ansible-role-ROLENAME/blob/docker-tests/test.yml) test environment. See the section Testing for details.

## Testing

There are two types of test environments available. One powered by Vagrant, another by Docker. The latter is suitable for running automated tests on Travis-CI. Test code is kept in separate orphan branches. For details of how to set up these test environments on your own machine, see the README files in the respective branches:

- Vagrant: [vagrant-tests](https://github.com/bertvv/ansible-role-ROLENAME/tree/vagrant-tests)
- Docker: [docker-tests](https://github.com/bertvv/ansible-role-ROLENAME/tree/docker-tests)

## Contributing

Issues, feature requests, ideas are appreciated and can be posted in the Issues section.

Pull requests are also very welcome. The best way to submit a PR is by first creating a fork of this Github project, then creating a topic branch for the suggested change and pushing that branch to your own fork. Github can then easily create a PR based on that branch. Don't forget to add your name to the contributor list below!

## License

2-clause BSD license, see [LICENSE.md](LICENSE.md)

## Contributors

- [Bert Van Vreckem](https://github.com/bertvv/) (maintainer of role skeleton)
- [Lennert Mertens](https://github.com/LennertMertens)
- [Ismail El Kaddourri](https://github.com/ismailelk)
