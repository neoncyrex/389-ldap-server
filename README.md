# 389-ldap-server
This role installs the 389-server (LDAP server)  on the target machine(s).

## Features
- Configuring single LDAP server
- Repcation support:
  - Configuring replication supplier
  - Configuring replication consumer
  - Multi Master replications

## Requirements
- Ansible version: 1.4 or higher
- OS: RHEL 7.x, CentOS 7.x
- Valid FQDN (hostname) is in place

## Role Variables
The variables that can be passed to this role and a brief description about them are as follows:

    ldap_password: Admin123
    ldap_suffix: dc=example,dc=com
    ldap_rootdn: cn=root
    serverid: ldapsrv

    admin_password: Admin123
    admin_domain: example.com

    enable_replication_supplier: false
    replication_nsds5replicaid: 7
    replication_agreement_name: ExampleAgreement
    replication_consumer_host: consumer.example.com

    enable_replication_consumer: false
    replication_user: replmanager
    replication_user_password: Admin123



## Usage

### 1. Configure an 389-server on the targed machine (variables in playbook):

> $ cat ldap.yaml
    
	- hosts: all

	  sudo: true

          roles:

		- { role: 389-ldap-server, admin_domain: example.com, admin_password: secret }


> $ ansible-playbook ldap.yaml




### 2. Configure an 389-server on the targed machine (variables in CLI):

> $ cat ldap.yaml
    
	- hosts: all

          sudo: true

          roles:

		- 389-ldap-server


> $ ansible-playbook -e 'admin_domain=example.com admin_password:secret' ldap.yaml


## Author Information
Name: Artemii Kropachev
