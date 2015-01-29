This is an [Ansible](http://www.ansible.com/home) role for installing
[Riemann dash](http://riemann.io).

You may also be interested in:

* an Ansible role for
  [Riemann](https://github.com/dhruvbansal/riemann-server-ansible-role),
  the Riemann server itself

# What it Does

## Software

Installs the `riemann-dash` gem which provides the `riemann-dash`
command, a thin wrapper around launching a
[Sinatra](http://www.sinatrarb.com/) web app.

## Configuration & Logging

Creates the files:

* `/etc/riemann/dash.rb` -- configuration file for Riemann dash
* `/etc/nginx/sites-available/riemann-dash.conf` -- configuration file for nginx
* `/var/log/riemann-dash` -- log directory for Sinatra & nginx
* `/etc/logstash/conf.d/riemann-dash.conf` -- configuration file for Logstash

## Services

On Ubuntu/Debian it creates an Upstart script
`/etc/init/riemann-dash.conf` which defines a system service
`riemann-dash` listening on port 5557.

# Usage

Use the role in a playbook like this:

```yaml
- hosts: all
  roles:
    - riemann-dash
```

Set the `riemann_dash_use_logstash` to `false` to skip the logstash
configuration.
