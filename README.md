# Ansible role `squirrelmail`

An Ansible role for PURPOSE. Specifically, the responsibilities of this role are to:

-

## Requirements

No specific requirements

## Role Variables


| Variable        | Default | Comments (type)  |
| :---            | :---    | :---             |
| `role_var`      | -       | (scalar) PURPOSE |
| domain          |localhost|How the email domain will be named|
|imapServerAddress|localhost|Server that provides IMAP services for Squirrelmail|
|smtpServerAddress|localhost|Server that provides SMTP services for Squirrelmail|
|default_language |en_US    |Language that will be used by Squirrelmail|


## Dependencies

- ![bertvv.mailserver](https://github.com/bertvv/ansible-role-mailserver)

- Ansible role ![bertvv.rhbase](https://github.com/bertvv/ansible-role-rh-base) can be used to open the necessary firewall ports and to create users for the mailserver.

- Ports to open:

```
  rhbase_firewall_allow_services:
    - pop3s
    - imaps
  rhbase_firewall_allow_ports:
    - 587/tcp
    - 465/tcp
    - 110/tcp
    - 143/tcp
```

- Users can be created using the following syntax.
This creates users that can login in to the mailserver but not into the linux machine.

```
  rhbase_users:
    - name: johndoe
      password: '$6$WIFkXf07Kn3kALDp$fHbqRKztuufS895easdT [...]'
      shell: /sbin/nologin
```


## Example Playbook

See the test playbooks in either the [Vagrant](https://github.com/bertvv/ansible-role-squirrelmail/blob/vagrant-tests/test.yml) or [Docker](https://github.com/bertvv/ansible-role-squirrelmail/blob/docker-tests/test.yml) test environment. See the section Testing for details.

## Testing

There are two types of test environments available. One powered by Vagrant, another by Docker. The latter is suitable for running automated tests on Travis-CI. Test code is kept in separate orphan branches. For details of how to set up these test environments on your own machine, see the README files in the respective branches:

- Vagrant: [vagrant-tests](https://github.com/bertvv/ansible-role-squirrelmail/tree/vagrant-tests)
- Docker: [docker-tests](https://github.com/bertvv/ansible-role-squirrelmail/tree/docker-tests)

## Contributing

Issues, feature requests, ideas are appreciated and can be posted in the Issues section.

Pull requests are also very welcome. The best way to submit a PR is by first creating a fork of this Github project, then creating a topic branch for the suggested change and pushing that branch to your own fork. Github can then easily create a PR based on that branch. Don't forget to add your name to the contributor list below!

## License

2-clause BSD license, see [LICENSE.md](LICENSE.md)

## Contributors

- [Bert Van Vreckem](https://github.com/bertvv/) (maintainer)
- [Robin Roelandt](https://github.com/RobinRoelandt)
- [Florian Van Steen](https://github.com/florianvansteen)
- [Jolan van Impe](https://github.com/jolanvanimpe)
