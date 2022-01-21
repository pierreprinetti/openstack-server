# openstack-server

A convenience script for creating a server in your OpenStack cloud, in its own
network, with its own security groups, exposed with a floating ip.

## Usage

```shell
openstack-server [-p] -f <flavor> -i <image> -e <external network> -k <key> <NAME>
```

**Required parameters:**

* `-f`: Flavor of the Compute instance
* `-i`: Image of the Compute instance
* `-e`: Name or ID of the public network where to create the floating IP
* `-k`: Name or ID of the SSH public key to add to the server
* `<NAME>`: name to give to the OpenStack resources

**Optional parameters:**

* `-p`: Do not clean up the server after creation (will print a cleanup script instead of executing it)

## Persistent configuration

The script will source a file in `${XDG_CONFIG_HOME:-${HOME}/.config}/openstack-server/${OS_CLOUD}.conf` before running, if it exists.
Any option passed through the configuration file are not required any more. Any options passed as flags will override the sourced configuration.

Here is an example valid configuration file:

```plaintext
server_flavor=m1.xlarge
server_image=fedora-35
external_network=external
key_name=mykey
```
