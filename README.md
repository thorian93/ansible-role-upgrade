# Ansible Role: Upgrade

This role performs upgrades on RHEL/CentOS, Debian/Ubuntu and Fedora servers.

## Here be Dragons!

The reboot check for apt is implemented via [needrestart](https://github.com/liske/needrestart). It checks for services that need a restart and newer kernels.
If it finds any of those a reboot will be performed, unless you disable it via the dedicated variable.

For Fedora this check is implemented through the dnf plugin [needs-restarting](https://dnf-plugins-core.readthedocs.io/en/latest/needs_restarting.html).
For RHEL/CentOS it is implemented through the [needs-restarting](https://dnf-plugins-core.readthedocs.io/en/latest/needs_restarting.html) tool.
For both Fedora and RHEL/CentOS a reboot will be performed based on the return code of the respective tool, unless you disable it via the dedicated role variable.

Neither of these methods are perfect but it works reasonably good. You might want to look through the role before using it though.

## Known issues

- CentOS 8: Reboot detection does not work as there is a flag missing for the dnf needs-restarting plugin. No reboot will be performed at any time.
- Fedora 30: Wrong dependency resolution inside Ansible causes trouble installing dependent tool. Has to be fixed by setting `ansible_python_interpreter` accordingly.
- **openSUSE Leap 15 and 42**: A missing dependency does not allow installation of a dependent tool. A workaround is in place. Also the upgrade process seems unstable. I will list these distributions as stable regarding below mentioned OS compatibility check anyway as currently the role does not seem to break stuff, but please be careful! Also feel free to give me a hint, if you know how to fix this stuff.

## Requirements

No special requirements; note that this role requires root access, so either run it in a playbook with a global `become: yes`, or invoke the role in your playbook like:

    - hosts: foobar
      roles:
        - role: ansible-role-upgrade
          become: yes

Also this role only **checks if the system is available at port 22** after a reboot. For further checks and monitoring refer to my [ansible-playbooks](https://github.com/thorian93/ansible-playbooks) repository and look for the example `ansible-role-upgrade.yml` and the corresponding `checkhost.yml` playbooks.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    upgrade_packages_on_hold: []

Set packages which you don't want to upgrade automatically on hold before upgrading.

    upgrade_unattended_reboot: "true"

Enable unattended reboot in case it is necessary after updates. Default is `true`, set to `false` to disable reboots.

    upgrade_force_reboot: "false"

Force a reboot of each server independent of the result of the reboot check. Default is `false`, set to `true` to enable forced reboots.

## Dependencies

None.

## OS Compatibility

This role ensures that it is not used against unsupported or untested operating systems by checking, if the right distribution name and major version number are present in a dedicated variable named like `<role-name>_stable_os`. You can find the variable in the role's default variable file at `defaults/main.yml`:

    upgrade_stable_os:
      - Debian 10
      - Ubuntu 18
      - CentOS 7
      - Fedora 30

If the combination of distribution and major version number do not match the target system, the role will fail. To allow the role to work add the distribution name and major version name to that variable and you are good to go. But please test the new combination first!

Kudos to [HarryHarcourt](https://github.com/HarryHarcourt) for this idea!

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

MIT

## Author Information

This role was created in 2019 by [Thorian93](http://thorian93.de/).
