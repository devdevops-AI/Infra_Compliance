# Infra_Compliance

Example Ansible playbooks that check and remediate a few RHEL 8 CIS controls.  The compliance check playbook records the status of each control and writes a simple HTML report using a Jinja2 template.

## Files

- `playbooks/rhel8_cis_check.yml` – runs several CIS checks and saves `/tmp/cis_report.html` on the target host.
- `playbooks/rhel8_cis_remediate.yml` – applies the fixes for those controls using Ansible tasks.
- `inventory.ini` – simple inventory pointing to localhost for testing.
- `templates/report.html.j2` – Jinja2 template used by the check playbook to generate the report.

## Usage

Run the compliance scan:

```bash
ansible-playbook -i inventory.ini playbooks/rhel8_cis_check.yml
```

After execution, open `/tmp/cis_report.html` on the target host to view the results.

Run the remediation playbook with:

```bash
ansible-playbook -i inventory.ini playbooks/rhel8_cis_remediate.yml
```

This applies the fixes defined in the playbook.
