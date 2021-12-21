[![CI](https://github.com/de-it-krachten/ansible-role-unbound/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-unbound/actions?query=workflow%3ACI)


# ansible-role-unbound

Installs & configures unbound 


Platforms
--------------

Supported platforms

- CentOS 7
- CentOS 8
- Debian 10 (Buster)
- Debian 11 (Bullseye)
- Ubuntu 18.04 LTS
- Ubuntu 20.04 LTS



Role Variables
--------------
<pre><code>
# Main configuration directory
unbound_etc_dir: /etc/unbound

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
# unbound_firewall_ports:
#   - { port: 53, proto: tcp }
#   - { port: 53, proto: udp }
unbound_firewall_ports: []
</pre></code>


Example Playbook
----------------

<pre><code>
- name: Converge
  hosts: all
  vars:
    unbound_do_ip6: false
    unbound_firewall_ports:
      - port: '53'
        proto: tcp
      - port: '53'
        proto: udp
  tasks:
    - name: Include role 'ansible-role-unbound'
      include_role:
        name: ansible-role-unbound
</pre></code>
