## Ansible Role: Consul

Ansible role to setup, manage consul cluster/standalone

Some of the highlighting features are:-

  - Cluster and Standalone setup of Consul cluster
  - Healthcheck integration for consul

This role supports Debian family right now, other OS support is under construction.

### Requirements

**No third party requirement is needed by this role**

### Roles Variables

Roles variables are categorized into two divisions i.e. Mandatory and Optional.

#### Mandatory Variables

|**Variables**|**Default Values**|**Possible Values**|**Type**|**Description**|
|-------------|------------------|-------------------|--------|---------------|
| consul_data_dir | `/opt/consul` | `Linux path` | string | Data directory for consul node |
| consul_data_dir | `/etc/consul.d` | `Linux path` | string | Configuration directory for consul node |
| consul_encryption_key | `qpDl5EBnz4+5yFBUDIGkxD8g2WRhROVOF7IcDHAccAw=` | `Base64 encoded key` | string | Encryption key for consul nodes |
| consul_datacenter_name | `new-jersey-primary` | `Any name` | string | Name of the datacenter for consul nodes |

#### Optional Variables

|**Variables**|**Default Values**|**Possible Values**|**Type**|**Description**|
|-------------|------------------|-------------------|--------|---------------|
| consul_version | `1.8.0` | `Consul version` | string | Consul version which needs to be installed |
| consul_log_level | `INFO` | <ul><li>TRACE</li><li>DEBUG</li><li>INFO</li><li>WARN</li><li>ERROR</li></ul> | string | Log level for consul service |
| client_addr | `0.0.0.0` | `IP Address` | IP | IP address to bind and listen consul service |


### Usage

The inventory for consul role should look like this:-

```ini
[consul]
consul-server1 ansible_ssh_host=54.212.217.221
consul-server2 ansible_ssh_host=54.189.50.237
consul-server3 ansible_ssh_host=54.244.160.224

[consul:vars]
ansible_ssh_user=ubuntu
```

An example playbook should look like this:-

```yaml
---
- hosts: consul
  roles:
    - consul
```

and for running the ansible role, we will use ansible cli.

```shell
ansible-playbook -i tests/inventory tests/test.yml
```
