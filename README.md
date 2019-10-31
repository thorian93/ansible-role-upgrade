# Ansible Role: Upgrade

This role performs upgrades on RHEL/CentOS, Debian/Ubuntu and Fedora servers.

## Requirements

No special requirements; note that this role requires root access, so either run it in a playbook with a global `become: yes`, or invoke the role in your playbook like:

    - hosts: foobar
      roles:
        - role: ansible-upgrade
          become: yes

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    upgrade_packages_on_hold: []

Set packages which you don't want to upgrade automatically on hold before upgrading.

## Dependencies

None.

## Example Playbook

    - hosts: foobar
      become: yes
      roles:
        - ansible-upgrade

## License

GPLv3

## Author Information

This role was created in 2019 by [Thorian93](https://thorian93.de/).
