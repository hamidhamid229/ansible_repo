# Ansible Project 

## Clone Repository

```bash
gh repo clone hamidhamid229/ansible_repo
cd ansible_repo
```

## Install Dependencies

```bash
pip3 install pipenv
pipenv install
pipenv shell
```

## Verify Ansible

```bash
ansible --version
```

## Verify Inventory

```bash
ansible-inventory -i inventories/ir-thr-si1/hosts --graph
```

## Symlink

`inventories/ir-thr-si1/group_vars/all.yml` points to:

```text
inventories/shared_vars/all.yml
```

Create the symlink:

```bash
ln -s ../../shared_vars/all.yml inventories/ir-thr-si1/group_vars/all.yml
```

If the file already exists:

```bash
rm inventories/ir-thr-si1/group_vars/all.yml
ln -s ../../shared_vars/all.yml inventories/ir-thr-si1/group_vars/all.yml
```

Verify:

```bash
ls -l inventories/ir-thr-si1/group_vars/
```

Expected:

```text
all.yml -> ../../shared_vars/all.yml
```

Check the target:

```bash
realpath inventories/ir-thr-si1/group_vars/all.yml
```

## Run Playbook

```bash
ansible-playbook \
  -i inventories/ir-thr-si1/hosts \
  playbooks/site.yml
```

> `Pipfile`, `Pipfile.lock`, and symlinks must be committed to Git.

