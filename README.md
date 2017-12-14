# Ansible role `squirrelmail`

An Ansible role which sets up squirrelmail on servers that run RedHat. Specifically, the responsibilities of this role are to:

- Install necessary packages
- Manage configuration
- Manage SELinux, when it is enabled

When the installation is completed, the homepage of squirrelmail can be seen on your hostmachine by following the link ```IP adress of your local machine/squirrelmail```

## Requirements

Ports required to be opened on the firewall (if you decide to use ![bertvv.rhbase](https://github.com/bertvv/ansible-role-rh-base)):

```
  rhbase_firewall_allow_services:
    - pop3s
    - imaps
    - httpd
```

Users can be created using the following syntax (if you decide to use ![bertvv.rhbase](https://github.com/bertvv/ansible-role-rh-base)).
The shell parameter creates users that can login on the squirrelmail webinterface but not into the linux machine.

```
  rhbase_users:
    - name: johndoe
      password: '$6$WIFkXf07Kn3kALDp$fHbqRKztuufS895easdT [...]'
      shell: /sbin/nologin
```


## Role Variables


| Variable        | Default | Comments (type)  |
| :---            | :---    | :---             |
|Squirrelmail_OrganizationName|SquirrelMail|The name of the organitation|
|Squirrelmail_signOutPage|/webmail|The page you will be redirected to when you sign out|
|Squirrelmail_domain|localhost|How the email domain will be named|
|Squirrelmail_sendmail|false|If set to true POP will be prefered over SMTP|
|Squirrelmail_imapServerAddress|localhost|Server that provides IMAP services for Squirrelmail|
|Squirrelmail_smtpServerAddress|localhost|Server that provides SMTP services for Squirrelmail|
|Squirrelmail_serverType|dovecot|Service used for IMAP services|
|Squirrelmail_defaultLanguage|en_US|Language that will be used by Squirrelmail|


## Dependencies

- ![bertvv.httpd](https://github.com/bertvv/ansible-role-httpd) provides PHP support for Squirrelmail.

- ![bertvv.mailserver](https://github.com/bertvv/ansible-role-mailserver) provides dovecot and postfix services required for Squirrelmail to work if Dovecot and Postfix are used. It is possible to use this role with antoher IMAP provider, which include: bincimap, courier, cyrus, dovecot, exchange, hmailserver, macosx, mercury32, uw, gmail, other. These services must be defined in the YML file the way they are written here.

- ![bertvv.rhbase](https://github.com/bertvv/ansible-role-rh-base) can be used to open the necessary firewall ports and to create users for the mailserver.


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
