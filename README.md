# Ansible Webserver Project — Runbook

## Prerequisites (control machine)
- Ansible installed (2.9+ recommended)
- SSH access to target hosts

## Quick run
1. Update `inventory/hosts.yaml` with your hosts and key paths.
2. Test connectivity:
   - `ansible -i inventory/hosts.yaml all -m ping -u <user> --private-key /path/to/key.pem`
3. Run playbook:
   - `ansible-playbook -i inventory/hosts.yaml playbooks/webserver.yaml -u <user> --private-key /path/to/key.pem`
4. Verify externally by visiting `http://<server-ip>` in a browser or from control host run:
   - `curl http://<server-ip>`

## Notes/Troubleshooting
- If SELinux prevents Apache from serving files, run the SELinux-related tasks manually or inspect `audit.log`.
- If `ufw` or `firewalld` are not present, firewall tasks are skipped gracefully.
