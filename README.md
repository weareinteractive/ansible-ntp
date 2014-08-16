# Ansible Ntp Role

[![Build Status](https://travis-ci.org/weareinteractive/ansible-ntp.png?branch=master)](https://travis-ci.org/weareinteractive/ansible-ntp)
[![Stories in Ready](https://badge.waffle.io/weareinteractive/ansible-ntp.svg?label=ready&title=Ready)](http://waffle.io/weareinteractive/ansible-ntp)

> `ntp` is an [ansible](http://www.ansible.com) role which: 
> 
> * installs ntp
> * configures ntp

## Installation

Using `ansible-galaxy`:

```
$ ansible-galaxy install franklinkim.ntp
```

Using `arm` ([Ansible Role Manager](https://github.com/mirskytech/ansible-role-manager/)):

```
$ arm install franklinkim.ntp
```

Using `git`:

```
$ git clone https://github.com/weareinteractive/ansible-ntp.git
```

## Variables

```
# ntp_servers:
#   - 0.de.pool.ntp.org
#   - 1.de.pool.ntp.org
#   - 3.de.pool.ntp.org
#   - 4.de.pool.ntp.org
#

# array of server addresses
ntp_servers: []
# start on boot
ntp_service_enabled: yes
# current state: started, stopped
ntp_service_state: started
#  drift file
ntp_driftfile: /var/lib/ntp/ntp.drift
# stats dir
ntp_statsdir: /var/log/ntpstats/
```

## Example playbook

```
- host: all
  roles: 
    - franklinkim.ntp
  vars:
    ntp_servers:
      - 0.de.pool.ntp.org
      - 1.de.pool.ntp.org
      - 3.de.pool.ntp.org
      - 4.de.pool.ntp.org
```

## Testing

```
$ git clone https://github.com/weareinteractive/ansible-ntp.git
$ cd ansible-ntp
$ vagrant up
```

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests and examples for any new or changed functionality.

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## License
Copyright (c) We Are Interactive under the MIT license.
