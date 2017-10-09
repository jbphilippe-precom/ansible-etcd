Role Name
=========

    Deploy etcd 3.x on Ubuntu (tested on 14.04 and 16.04)

Requirements
------------

  Ansible 2.x

Role Variables
--------------
    etcd_version: 3.0.3
    etcd_download_url: "https://mirror.services.local/etcd/archive/v{{ etcd_version }}/etcd-v{{ etcd_version }}-linux-amd64.tar.gz"
    etcd_download_output_file: "etcd-v{{ etcd_version }}-linux-amd64.tar.gz"
    etcd_extracted_dir: etcd-v{{ etcd_version }}-linux-amd64
    etcd_var_path: /var/lib/etcd/
    etcd_log_path: /var/log/etcd/
    etcd_group: etcd
    etcd_user: etcd
    etcd_clustername: "MonCluster"

    ## template ##
    etcd_init_file_trusty: "init_etcd.conf"
    etcd_default_file_trusty: default_etcd_trusty
    etcd_init_file_xenial: "etcd.service"
    etcd_default_file_xenial: default_etcd_xenial
    etcd_logrotate: "etcd_logrotate"

    ## dest of template ##
    etcd_default_file_dest: /etc/default/etcd
    etcd_init_file_dest_trusty: "/etc/init/etcd.conf"
    etcd_init_file_dest_xenial: "/etc/systemd/system/etcd.service"
    etcd_logrotate_dest: "/etc/logrotate.d/etcd"


    ## here name of your host group in inventory ##
    etcd_inventory_clustergroup: "myhostsgroup"
    etcd_admin_password: "Chang3It"

Dependencies
------------

    None

Example Playbook
----------------

    - hosts: graylogserver
      become: yes
      roles:
        - { role: ansible-etcd }
      vars:
        etcd_version: 3.0.3
        etcd_clustername: "MonClusterEtcd"
        etcd_inventory_clustergroup: "graylogserver"
        etcd_admin_password: "42xordcte"

License
-------

D

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
