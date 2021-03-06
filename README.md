UFW
===

This role configure firewall rules through UFW

Requirements
------------

- iptables

Supported distributions
-----------------------

- Debian: 
    - Jessie (8)
    - Stretch (9)

Default variables
--------------

```yaml
# "ufw_ssh_port"
# Default port for SSH
# Default: ssh_port if defined or 22
ufw_ssh_port: "{{ ssh_port | default(22) }}"

# "ufw_ssh_allowed_ips"
# Allowed IPs for SSH in
# Default: not defined
# Required: true
#
#ufw_ssh_allowed_ips:
#  - 0.0.0.0/0 # Allow all IPs, not recommended

# "ufw_http_s_allowed_ips"
# Allowed IPs for HTTP(S)
# You can use this to restrict access to certain IPs only
# Default: not defined
#
#ufw_http_s_allowed_ips:
#  - 0.0.0.0/0 # (All IPs)

# "ufw_openvpn_allowed_ips"
# Allowed IPs for OpenVPN
# You can use this to restrict access to certain IPs only
# Default: not defined
#
#ufw_openvpn_allowed_ips:
#  - 0.0.0.0/0 # (All IPs)

# "ufw_openvpn_port"
# Default port for OpenVPN
# Default: openvpn_port if defined or 1194
ufw_openvpn_port: "{{ openvpn_port | default(1194) }}"

# "ufw_openvpn_proto"
# Default proto for OpenVPN
# Default: openvpn_proto if defined or udp
ufw_openvpn_proto: "{{ openvpn_proto | default('udp') }}"

# "ufw_custom_rules"
# Custom host firewall rules to add to default firewall configuration
# Default: empty list
#ufw_custom_rules:
#
#  - {
#    rule: allow, # omitted if not specified
#    port: 23, # omitted if not specified
#    direction: in, # in or out, omitted if not specified
#    interface: eth0, # omitted if not specified
#    src: 0.0.0.0/0, # omitted if not specified
#    dest: 0.0.0.0/0, # omitted if not specified
#    proto: tcp # omitted if not specified
#  }
#  - {
#    rule: allow,
#    port: 8080,
#    src: 0.0.0.0/0,
#    proto: tcp
#  }

# "ufw_group_custom_rules"
# Custom host group firewall rules to add to default firewall configuration
# Default: empty list
#ufw_group_custom_rules:
#
#  - {
#    rule: allow, # omitted if not specified
#    port: 23, # omitted if not specified
#    direction: in, # in or out, omitted if not specified
#    interface: eth0, # omitted if not specified
#    src: 0.0.0.0/0, # omitted if not specified
#    dest: 0.0.0.0/0, # omitted if not specified
#    proto: tcp # omitted if not specified
#  }
#  - {
#    rule: allow,
#    port: 18573,
#    direction: out,
#    dest: 0.0.0.0/0,
#  }

# "ufw_bitbucket_allowed"
# Allow or deny SSH connections to Bitbucket servers
# Default: false
#
ufw_bitbucket_allowed: false

# "ufw_bitbucket_ips"
# Bitbucket IPs we need to authorize to be able to run git clone
#
ufw_bitbucket_ips:
  - 104.192.143.1
  - 104.192.143.2
  - 104.192.143.3
  - 104.192.143.65
  - 104.192.143.66
  - 104.192.143.67

# "ufw_github_allowed"
# Allow or deny SSH connections to Github servers
# Default: true
#
ufw_github_allowed: true

# "ufw_github_meta_endpoint"
# Github API endpoint to retrieve git servers IPs
ufw_github_meta_endpoint: https://api.github.com/meta

# "ufw_logging"
# Toggles UFW logging. Logged packets use the LOG_KERN syslog facility.
# Default: low
# Could be on, off, low, medium, high, full
#
ufw_logging: low
```

Dependencies
------------

None

Tests
-----

```
$ cd tests
$ vagrant up --provision 
```
