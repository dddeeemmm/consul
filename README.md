Consul
=========

    Install and configure Consul (https://consul.io)
    https://galaxy.ansible.com/dddeeemmm/consul


Requirements
----------------

    This role requires root privileges, so tell ansible to use become: true in any convenient way for you


Role Variables
--------------

    project_name:       # [default: {{ ansible_fqdn.split ('.', 2) [1] }} | aliace: {{ os_project_name }}] second.DNS.part
    project_domain:     # [required] main domain
                        # [!] definition this var in inventory or group | host vars

    consul_localrepo:   # [default: false] use local rpm repository
    consul_version:     # [default: 1.6.2] when consul_localrepo: false 
    
    consul_mode:        # [default: client] client | server
    consul_use_tls:     # [default: true] true | false 
    consul_acl_enable:  # [default: true] true | false
    consul_ca_file:     # [default: files/certs/cacert.{{ project_domain }}.pem]
    consul_cert_file:   # [default: files/certs/wildcard.{{ os_project_name }}.{{ project_domain }}.crt] 
    consul_key_file:    # [default: files/certs/wildcard.{{ os_project_name }}.{{ project_domain }}.key]


Example Playbook
----------------

    tests/test.yml


Example Run
----------------

    ansible-playbook test/test.yml -e project_name=dev -e project_domain=name.org -i test/inventory
    ansible-playbook test/test.yml -e project_name=dev -e project_domain=name.org -e consul_localrepo=false -i test/inventory


License
-------

    MIT


Author Information
------------------

    Dmitrij Petrov
