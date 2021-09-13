# Ansible Role: Swap Partition

An [Ansible Galaxy](https://galaxy.ansible.com/) role for creating a swap partition using an existing block device node.

## Requirements

* An existing block device node for a disk partition (e.g. `/dev/xvdb`) that will be formatted and used for swap space

## Role Variables

### Mandatory variables

Only the single `swap_partition_device_node` path variable is mandatory, all other variables are optional and have sensible default values (see `defaults/main.yml`):

```yaml
swap_partition_device_node: /dev/xvdb
```

:warning: This block device will be formatted by this role so please exercise caution.

### Optional variables

To specify mount options for the swap device:

```yaml
swap_partition_mount_options: ...
```

To disable the swap partition if it was previously enabled (the `fstab` entry will be removed if it exists and the swap partition disabled):

```yaml
swap_partition_enabled: no
```

## Example Requirements File

```yaml
- src: https://github.com/companieshouse/ansible-role-swap-partition
  name: swap-partition
  version: "n.n.n"
```

## Example Playbook

```yaml
    - hosts: all
      roles:
        - swap-partition
      vars:
        - swap_partition_device_node: /dev/xvdb
```

## License

MIT
