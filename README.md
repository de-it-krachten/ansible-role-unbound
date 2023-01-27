[![CI](https://github.com/de-it-krachten/ansible-role-unbound/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-unbound/actions?query=workflow%3ACI)


# ansible-role-unbound

Installs & configures unbound 



## Dependencies

#### Roles
None

#### Collections
- community.general

## Platforms

Supported platforms

- Red Hat Enterprise Linux 7<sup>1</sup>
- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- CentOS 7
- RockyLinux 8
- RockyLinux 9
- OracleLinux 8
- OracleLinux 9
- AlmaLinux 8
- AlmaLinux 9
- Debian 10 (Buster)
- Debian 11 (Bullseye)
- Ubuntu 18.04 LTS
- Ubuntu 20.04 LTS
- Ubuntu 22.04 LTS
- Fedora 36
- Fedora 37
- Alpine 3

Note:
<sup>1</sup> : no automated testing is performed on these platforms

## Role Variables
### defaults/main.yml
<pre><code>
# Main configuration directory
unbound_etc_dir: /etc/unbound

# Drop-in configuration directory
unbound_confd_dir: "{{ unbound_etc_dir }}/unbound.conf.d"

# Root hints file
unbound_hints_local: "{{ unbound_etc_dir }}/root.hints"

# Root hints url tfor downloading it
unbound_hints_url: https://www.internic.net/domain/named.cache

# Use IPv6
unbound_do_ip6: 'yes'

# Interface to listen on
unbound_interface: 127.0.0.1

# List of ACLs
unbound_access_control: []

# List of forward zone
unbound_forward_zones: []

# List of custom records (name, ip, cnames)
unbound_custom_records: []

# Lsit of local zones
unbound_local_zones:
  - 10.in-addr.arpa
  - 16.172.in-addr.arpa
  - 17.172.in-addr.arpa
  - 18.172.in-addr.arpa
  - 19.172.in-addr.arpa
  - 20.172.in-addr.arpa
  - 21.172.in-addr.arpa
  - 22.172.in-addr.arpa
  - 23.172.in-addr.arpa
  - 24.172.in-addr.arpa
  - 25.172.in-addr.arpa
  - 26.172.in-addr.arpa
  - 27.172.in-addr.arpa
  - 28.172.in-addr.arpa
  - 29.172.in-addr.arpa
  - 30.172.in-addr.arpa
  - 31.172.in-addr.arpa
  - 168.192.in-addr.arpa

# List of packages to instll
unbound_packages:
  - unbound
  - expat

# Name of the service
unbound_service: unbound

# Firewall active
unbound_firewall: true

# Firewall ports to open
unbound_firewall_ports:
  - { port: 53, proto: tcp }
  - { port: 53, proto: udp }
</pre></code>


### vars/family-RedHat.yml
<pre><code>
# Drop-in configuration directory
unbound_confd_dir: "{{ unbound_etc_dir }}/conf.d"
</pre></code>

### vars/default.yml
<pre><code>

</pre></code>

### vars/Alpine.yml
<pre><code>
# Drop-in configuration directory
unbound_confd_dir: "{{ unbound_etc_dir }}/conf.d"
</pre></code>

### vars/family-Debian.yml
<pre><code>
# Drop-in configuration directory
unbound_confd_dir: "{{ unbound_etc_dir }}/conf.d"
</pre></code>



## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'unbound'
  hosts: all
  become: "yes"
  vars:
    unbound_do_ip6: no
    unbound_firewall: False
    unbound_custom_records: [{'name': 'server1.example.com', 'ip': '192.168.56.100', 'cnames': ['test.example.com', 'test1.example.com']}, {'name': 'server2.example.com', 'ip': '192.168.56.101'}]
  tasks:
    - name: Include role 'unbound'
      ansible.builtin.include_role:
        name: unbound
</pre></code>
