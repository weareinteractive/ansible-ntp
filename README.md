# Ansible weareinteractive.ntp role

[![Build Status](https://img.shields.io/travis/weareinteractive/ansible-ntp.svg)](https://travis-ci.org/weareinteractive/ansible-ntp)
[![Galaxy](http://img.shields.io/badge/galaxy-weareinteractive.ntp-blue.svg)](https://galaxy.ansible.com/weareinteractive/ntp)
[![GitHub Tags](https://img.shields.io/github/tag/weareinteractive/ansible-ntp.svg)](https://github.com/weareinteractive/ansible-ntp)
[![GitHub Stars](https://img.shields.io/github/stars/weareinteractive/ansible-ntp.svg)](https://github.com/weareinteractive/ansible-ntp)

> `weareinteractive.ntp` is an [Ansible](http://www.ansible.com) role which:
>
> * installs ntp
> * configures ntp

**Note:**

> Since Ansible Galaxy supports [organization](https://www.ansible.com/blog/ansible-galaxy-2-release) now, this role has moved from `franklinkim.ntp` to `weareinteractive.ntp`!

## Installation

Using `ansible-galaxy`:

```shell
$ ansible-galaxy install weareinteractive.ntp
```

Using `requirements.yml`:

```yaml
- src: weareinteractive.ntp
```

Using `git`:

```shell
$ git clone https://github.com/weareinteractive/ansible-ntp.git weareinteractive.ntp
```

## Dependencies

* Ansible >= 2.4

## Variables

Here is a list of all the default variables for this role, which are also available in `defaults/main.yml`.

```yaml
---
# For more information about default variables see:
# http://www.ansibleworks.com/docs/playbooks_variables.html#id26
#

# package name (version)
ntp_package: ntp
# list of server
ntp_servers:
 - 0.ubuntu.pool.ntp.org
 - 1.ubuntu.pool.ntp.org
 - 2.ubuntu.pool.ntp.org
 - 3.ubuntu.pool.ntp.org
 - ntp.ubuntu.com
# list of peer hosts (typically on the same network)
ntp_peers: []
# start on boot
ntp_service_enabled: yes
# current state: started, stopped
ntp_service_state: started
#  drift file
ntp_driftfile: /var/lib/ntp/ntp.drift
# stats dir
ntp_statsdir: /var/log/ntpstats/

```

## Handlers

These are the handlers that are defined in `handlers/main.yml`.

```yaml
---
# For more information about handlers see:
# http://www.ansibleworks.com/docs/playbooks.html#handlers-running-operations-on-change

- name: restart ntp
  service: name=ntp state=restarted
  when: ntp_service_state != 'stopped'

```


## Usage

This is an example playbook:

```yaml
---

- hosts: all
  roles:
    - weareinteractive.ntp
  vars:
    ntp_servers:
      - 0.de.pool.ntp.org
      - 1.de.pool.ntp.org
      - 3.de.pool.ntp.org
      - 4.de.pool.ntp.org
    ntp_peers:
      - 127.0.0.4

```


## Testing

```shell
$ git clone https://github.com/weareinteractive/ansible-ntp.git
$ cd ansible-ntp
$ make test
```

## Contributing
In lieu of a formal style guide, take care to maintain the existing coding style. Add unit tests and examples for any new or changed functionality.

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

*Note: To update the `README.md` file please install and run `ansible-role`:*

```shell
$ gem install ansible-role
$ ansible-role docgen
```

## License
Copyright (c) We Are Interactive under the MIT license.
