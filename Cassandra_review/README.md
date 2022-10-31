Cassandra Setup
=========

This role is to install cassandra and setup cluster

Requirements
------------
* Java 8

Supported OS
------------
  * Ubuntu
  * RedHat

Role Variables
--------------
|**Variables**| **Default Values**| 
|----------|---------|
| version | 4.0.6 | 
| group_name | cassandra | 
| user_name | cassandra | 
| cassandra_home | /opt/cassandra |
| cassandra_path | /opt/cassandra/bin | 
| cassandra_data_directory | /var/lib/cassandra/data | 
| cassandra_hints_directory | /var/lib/cassandra/data/hints | 
| cassandra_commitlog_directory | /var/lib/cassandra/data/commitlogs | 
| cassandra_saved_caches_directory | /var/lib/cassandra/data/saved_caches | 
| cluster_name | 'Test Cluster' | 
| num_tokens | 16 | 
| allocate_tokens_for_local_replication_factor | 3 |
| seeds | "127.0.0.1:7000" | 
| storage_port | 7000 |  
| ssl_storage_port | 7001 | 
| listen_address | localhost | 
| native_transport_port | 9042 | 
| rpc_address | localhost |   


Inventory
----------
For cluster: An inventory should look like this:-
```ini
[seed-nodes]                 
seed1 xxx.xxx.xxx.xxx   ansible_user=xyz
seed2 xxx.xxx.xxx.xxx   ansible_user=xyz 
seed3 xxx.xxx.xxx.xxx   ansible_user=xyz 
```

Example Playbook
----------------
```
- name: INSTALL CASSANDRA & CONFIGURE IT 
   hosts: all
   become: true
   roles:
    - role: cassandra
```

Author Information
------------------

[Aakash Singh](https://gitlab.com/aakash894)