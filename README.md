# cloudev
Ansible script to create cloud dev environment for fresh cloud servers 

## What it Does

* Creates a non-root user with specified password and adds to sudoers
* Disables root ssh access
* Diables password authentication on ssh
* Installs and configures ufw
    * Only allows http, https and ssh
* Installs and configures fail2ban, installs whois as well
* Installs rkhunter
* Installs Postfix
* Installs and configures logwatch
    * Changes cron to weekly
* Installs my development environment
    * Installs dev packages
    * Installs my dotfiles and other config settings


### Prerequisites

* [Ansible](https://www.ansible.com/) is required on local machine
* Account on a cloud prodvider - Digital Ocean is the only provider that has been tested 

### Setup

Spin up a new server on your cloud provider with your ssh key tied to the root user.

You will need a password for your new non-root user that will be generated on your new cloud server:

```
pip install passlib
python -c "from passlib.hash import sha512_crypt; import getpass; print sha512_crypt.encrypt(getpass.getpass())"
```

Copy group_vars/cloud_servers_example to group_vars/cloud_servers and change variables.  Add the above generated password as well.

Copy hosts_example to hosts and update ip addresses to the generated cloud servers.

## Deployment

```
ansible-playbook playbook.yml -u root
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details

## Acknowledgments

* [Sovereign](https://github.com/sovereign/sovereign)
* [Mathias Bynens Dotfiles](https://github.com/mathiasbynens/dotfiles)

