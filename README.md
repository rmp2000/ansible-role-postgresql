# PostgreSQL Ansible Role

Ansible role to install and configure PostgreSQL on Debian-based systems.

## Role variables

```yaml
postgresql_version: "14"
postgresql_database: appdb
postgresql_user: appuser
postgresql_password: "set-a-secret-value"
postgresql_port: 5432
postgresql_listen_addresses: "*"
postgresql_pg_hba_address: "0.0.0.0/0"
```

## Requirements

The role uses the `community.postgresql` collection. Install it with:

```bash
ansible-galaxy collection install community.postgresql
```

## Local validation

From the repository root, install the declared collection and run the syntax check:

```bash
ansible-galaxy collection install -r requirements.yml
ansible-playbook --syntax-check tests/test.yml
```

To apply the role to a test Ubuntu host, provide a non-production password and run:

```bash
ansible-playbook -i <host>, tests/test.yml -e postgresql_password="test-only-password"
```

The role is intended to be imported into Ansible Galaxy as `rmp2000.postgresql` after review.

## Example playbook

```yaml
- hosts: database
  become: true
  roles:
    - role: postgresql
```
