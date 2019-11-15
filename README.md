# Ansible Role: Upgrade

This role performs upgrades on RHEL/CentOS, Debian/Ubuntu and Fedora servers.

## Requirements

No special requirements; note that this role requires root access, so either run it in a playbook with a global `become: yes`, or invoke the role in your playbook like:

    - hosts: foobar
      roles:
        - role: ansible-role-upgrade
          become: yes

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    upgrade_packages_on_hold: []

Set packages which you don't want to upgrade automatically on hold before upgrading.

    upgrade_unattended_reboot: "true"
Default is true, set to false if you do not want to reboot automatically after installing updates which require reboot.

## Dependencies

None.

## Example Playbook

    - hosts: foobar
      become: yes
      roles:
        - ansible-role-upgrade

## Contributing

Please feel free to open issues if you find any bugs, problems or if you see room for improvement. Also feel free to contact me anytime if you want to ask or discuss something.

## Disclaimer

This role is provided AS IS and I can and will not guarantee that the role works as intended, nor can I be accountable for any damage or misconfiguration done by this role. Study the role thoroughly before using it.

## License

GPLv3

## Author Information

This role was created in 2019 by [Thorian93](https://thorian93.de/).
