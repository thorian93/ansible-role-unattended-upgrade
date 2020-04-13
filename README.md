# Ansible Role: Unattended Upgrade

This role configures unattended upgrades on RHEL/CentOS, Debian/Ubuntu and Fedora servers.

This role is based on the work of @jnv and @samdoran. I am just trying to tie both roles together for simplicity.

Have a look at their distinct roles [ansible-role-unattended-upgrades](https://github.com/jnv/ansible-role-unattended-upgrades) and [ansible-role-yum-cron](https://github.com/samdoran/ansible-role-yum-cron).

## Here be Dragons!

Be sure to review the variables of this role carefully! The upstream maintainers did an awesome job making their roles stable and secure, but it is up to you to configure the role properly for your needs.

## Known issues

None.

## Requirements

No special requirements; note that this role requires root access, so either run it in a playbook with a global `become: yes`, or invoke the role in your playbook like:

    - hosts: foobar
      roles:
        - role: ansible-role-unattended-upgrade
          become: yes

## Role Variables

Available variables can be found in `defaults/main.yml`. There are many currently to list them all here.

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

    ---
    - name: "Run role."
      hosts: all
      become: yes
      roles:
        - ansible-role-unattended-upgrade

## Contributing

Please feel free to open issues if you find any bugs, problems or if you see room for improvement. Also feel free to contact me anytime if you want to ask or discuss something.

## Disclaimer

This role is provided AS IS and I can and will not guarantee that the role works as intended, nor can I be accountable for any damage or misconfiguration done by this role. Study the role thoroughly before using it.

## License

MIT

## Author Information

This role was created in 2020 by [Thorian93](http://thorian93.de/).
