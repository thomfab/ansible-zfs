Add ZFS to a server
===================

This role install ZFS on an ubuntu server

Role Variables
--------------

Along with ZFS, a periodic scrub script is added. Some variables give you control on when the script is run

Define the time when the ZFS scrub script is launched
  zfs_scrub_hour: "11"
  zfs_scrub_minute: "0"

Define the weekday for ZFS scrub script (see crontab for possible values)
  zfs_scrub_weekday: "1"

It is also possible to add a check_zpool command to the nagios nrpe plugin. If you enable this, be sure to also configure nagios nrpe on your server (for example : https://galaxy.ansible.com/list#/roles/2567)
  zfs_nagios_enabled: true
  zfs_zpoolname: "/tank"


Example Playbook
----------------

Example :

    ---
    - hosts: servers
      roles:
        - role: thomfab.ansible-zfs
          zfs_scrub_hour: "11"
          zfs_scrub_minute: "0"
          zfs_scrub_weekday: "1"
          zfs_nagios_enabled: true
          zfs_zpoolname: "/tank"


License
-------

BSD
