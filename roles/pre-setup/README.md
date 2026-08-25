# Pre-Setup Role

The `pre-setup` role prepares hosts for further configuration.
The entry point is `playbooks/site.yml`.

## Execution Order

The role runs tasks in the following order:

```text
delete_user
→ dns
→ update_upgrade
→ disable_auto_update
→ create_user
→ timezone
→ hostname
→ apps
→ permission_directory
```

## Tasks

* **delete_user** — Removes users with UID `>= 1000`, except users listed in `myusers`.
* **dns** — Replaces `/etc/resolv.conf` with the configured DNS settings.
* **update_upgrade** — Updates and upgrades the system packages.
* **disable_auto_update** — Disables automatic package updates.
* **create_user** — Creates users defined in `usermgmt`.
* **timezone** — Sets the timezone to `Asia/Tehran`.
* **hostname** — Sets the hostname to `pc1`.
* **apps** — Installs packages defined in `apps`.
* **permission_directory** — Sets ownership and permissions for paths defined in `permission_directory`.

## Run a Specific Tag

To run only a specific task:

```bash
ansible-playbook -i inventories/ir-thr-si1/hosts playbooks/site.yml --tags dns
```

For example:

```bash
ansible-playbook -i inventories/ir-thr-si1/hosts playbooks/site.yml --tags create_user
```

## Variables

Shared variables are defined in:

```text
inventories/shared_vars/all.yml
```
