# Ansible Role: Sidecar

[![Build Status](https://travis-ci.org/mklettner/ansible-role-sidecar.svg?branch=master)](https://travis-ci.org/mklettner/ansible-role-sidecar)

Installs and configures Graylog Sidecar Collector on RedHat/CentOS Linux servers.

Installation options:
- latest version (pulled from official github repository)
- specific version (pulled from official github repository) 
- local rpm (copied from files directory to remote server)





**Note**: This role is still work in progress

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):
 
    
    sidecar_server_url: http://127.0.0.1:9000/api/
    sidecar_update_interval: 10
    sidecar_tls_skip_verify: false
    sidecar_send_status: true
    sidecar_list_log_files: /var/log
    sidecar_node_id: graylog-collector-sidecar
    sidecar_collector_id: file:/etc/graylog/collector-sidecar/collector-id
    sidecar_cache_path: /var/cache/graylog/collector-sidecar
    sidecar_log_path: /var/log/graylog/collector-sidecar
    sidecar_log_rotation_time: 86400
    sidecar_log_max_age: 604800
    
    sidecar_tags: ['linux', 'apache']
    
    sidecar_backends:
             - {name: nxlog, enabled: false, binary_path: /usr/bin/nxlog, configuration_path: /etc/graylog/collector-sidecar/generated/nxlog.conf}
             - {name: filebeat, enabled: true, binary_path: /usr/bin/filebeat, configuration_path: /etc/graylog/collector-sidecar/generated/filebeat.yml}


If you like to install a specific version instead of the latest version, set `sidecar_version: X.Y.Z`.

     sidecar_version: 0.1.5
        
        

If you like to install a local rpm, place it in the files directory and set `sidecar_local_package: 'collector-sidecar-X.Y.Z-1.x86_64.rpm'` .

     sidecar_local_package: collector-sidecar-0.1.5-1.x86_64.rpm


## Dependencies

None.

## Example Playbook

    ---
    - hosts: all
      roles:
        - role: sidecar
          sidecar_server_url: https://example.com:9000/api/
          sidecar_update_interval: 20
          sidecar_backends:
                     - {name: filebeat, enabled: true, binary_path: /usr/bin/filebeat, configuration_path: /etc/graylog/collector-sidecar/generated/filebeat.yml}


## License

MIT / BSD

## Author Information

This role was created in 2018 by Matthias Klettner.
