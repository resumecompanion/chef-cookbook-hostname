# hostnames cookbook

## Description

Sets hostname and FQDN of the node. The latest code is hosted at
https://github.com/nathantsoi/chef-cookbook-hostname

## Attributes

- `node['set_fqdn']` - FQDN to set.

The asterisk character will be replaced with `node.name`. This way,
you can add this to base role:

```ruby
default_attributes :set_fqdn => '*.project-domain.com'
```

and have node set its FQDN and hostname based on its chef node name
(which is provided on `chef-client` first run's command line).

- `node['hostname_cookbook']['use_node_ip']` -- when true
  sets the hostname to ```node["ipaddress"]``` in ```/etc/hosts``` (default: `false`)

- `node['hostname_cookbook']['hostsfile_ip']` -- IP used in
  `/etc/hosts` to correctly set FQDN (default: `127.0.1.1`)


## Recipes

* `hostnames::default` -- will set node's FQDN to value of `set_fqdn` attribute,
and hostname to its host part (up to first dot).
* `hostnames::vmware` -- sets hostname automatically using vmtoolsd.
You do not need to set `node["set_fqdn"]`.

## Author

Maciej Pasternacki maciej@3ofcoins.net
Nathan nathan@veretile.com
