# Ansible Role: Kibana

An Ansible Role that installs Kibana on RedHat/CentOS.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```
kibana_version: "7.x"
kibana_dversion: "7.11.2"
```

The version of kibana to install.

```
kibana_package: kibana
kibana_package_state: present
```

The template to use for the Kibana config file, and the path to which the config file will be written.

```
kibana_server_port: 5601
kibana_server_host: "0.0.0.0"
```

The FQDN or IP address and port Kibana should use.

```
kibana_elasticsearch_url: "http://localhost:9200"
```

The URL (including port) over which Kibana will connect to Elasticsearch.

```
kibana_elasticsearch_username: ""
kibana_elasticsearch_password: ""
```

If Elasticsearch is protected by HTTP basic authentication, set the username and password so Kibana can connect.

## Dependencies

None.

## Example Playbook

```
- hosts: kibana
  roles:
    - clay_wangzhi.kibana
  vars:
    kibana_version: "7.x"
    kibana_dversion: "7.11.2"
    kibana_server_host: "{{ansible_ssh_host}}"
    kibana_server_name: "{{inventory_hostname}}"
    kibana_elasticsearch_url: '["http://172.16.91.27:9200", "http://172.16.91.1:9200", "http://172.16.91.151:9200"]'
```

## License

MIT / BSD