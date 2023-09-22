# Ansible role: KERNEL

Install the Linux kernel and setup sysctl and modprobe.

sysctl is inspired from [robertdebock](https://github.com/robertdebock/ansible-role-sysctl).

## Usage
Override [defaults](https://github.com/lunics/ansible_role_kernel/tree/main/defaults/main) following the examples below.

```yaml
sysctl_settings:
  - name:  vm.swapiness
    value: 60

modprobe:                 # load modules during the live system, not persistent
  - name: zfs
  - name: foo
    parameter: bar
    state: present
modules_load_d: []        # load modules at boot time, persistent
  - name: module_a
    parameter: env=1
modprobe_d_blacklist: []  # blacklist modules at boot
  - name: nouveau
modprobe_d_option:  []    # define parameters to listed modules
  - name:
    parameter:
modprobe_d_alias:  []     # define alias modules, TODO
modprobe_reboot: false
```
### TODO:
- setup permanent sysctl in /etc/sysctl.conf
- fix delegate_to: localhost on asserts
