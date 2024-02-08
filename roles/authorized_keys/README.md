# authorized_keys
Deploy ssh pub keys to hosts

# variables:

* `authorized_keys_base_list` contains the users which should be added to all systems.
* `authorized_keys_additional` can used to add additional users by the playbook
* `authorized_keys_user` to define the user. Default: root

