PgAdmin
=========

Ansible role to deploy PgAdmin to a Kubernetes Cluster

Requirements
------------

This role is intended to work with the deployment script of GeoGeekSuite.
It requires a running Kubernetes cluster.

Role Variables
--------------

manifest_folder
gisnamespace
geodatabase
  pgadmin
    mail
    pw

Dependencies
------------

None

Example Playbook
----------------

---
- hosts: local
  vars_prompt:
    - name: password
      prompt: Set a password?
  vars:
    manifest_folder: ~/geogeek_manifests
    gisnamespace: gis
    pgadmin:
      container_image: dpage/pgadmin4
      container_version: '6.12'
      mail: me@geogeeksuite.com
      pw: '{{ password }}'
  roles:
  - { role: pgadmin,
        tags: pgadmin }

License
-------

Apache, Version 2.0

Author Information
------------------

Marco Bradtke
www.geogeeksuite.com