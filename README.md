Cassandra Setup
=========

This role is to install cassandra and setup cluster

Requirements
------------
* Java 8 or 11
* Python 2.6+ [For cqlsh]

Supported OS
------------
  * Ubuntu
  * RedHat

Role Variables
--------------
|**Variables**| **Default Values**| 
|----------|---------|
| version | 4.0.6 |
| mode | 0755 | 
| group_name | cassandra | 
| user_name | cassandra | 
| cassandra_home | /opt/cassandra |
| cassandra_path | /opt/cassandra/bin | 
| cassandra_data_directory | /var/lib/cassandra/data | 
| cassandra_hints_directory | /var/lib/cassandra/data/hints | 
| cassandra_commitlog_directory | /var/lib/cassandra/data/commitlogs | 
| cassandra_saved_caches_directory | /var/lib/cassandra/data/saved_caches | 
| cluster_name | Mycluster | 
| num_tokens | 16 | 
| allocate_tokens_for_local_replication_factor | 3 |
| seeds | nodes ipv4 | 
| storage_port | 7000 |  
| ssl_storage_port | 7001 | 
| listen_address | default ipv4 address | 
| native_transport_port | 9042 | 
| rpc_address | localhost |   
| endpoint_snitch | GossipingPropertyFileSnitch |

Directory Layout
----------------
```
cassandra
.
├── files
│   └── cassandra.service
├── handlers
│   └── main.yml
├── meta
│   └── main.yml
├── tasks
│   ├── debian.yml
│   ├── main.yml
│   └── redhat.yml
├── templates
│   └── cassandra.yaml.j2
└── vars
    └── main.yml

6 directories, 8 files

```
Inventory
----------
For cluster: An inventory should look like this:-
```ini
[seed-nodes]                 
seed1 xxx.xxx.xxx.xxx   ansible_user=xyz
seed2 xxx.xxx.xxx.xxx   ansible_user=xyz 
seed3 xxx.xxx.xxx.xxx   ansible_user=xyz 
```
where, The seed-nodes group contains the details of the nodes we want to cluster.

For standalone: An inventory should look like this:-
```ini
[seed-nodes]                 
seed1 xxx.xxx.xxx.xxx  ansible_user=xyz
```

Example Playbook
----------------
```
- name: INSTALL CASSANDRA & CONFIGURE IT 
   hosts: seed-nodes
   become: true
   roles:
      - role: '../cassandra'
```

Author Information
------------------

[Aakash Singh](https://gitlab.com/aakash894)
