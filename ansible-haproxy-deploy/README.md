# Ansible HAProxy Deployment

This project provides an Ansible playbook to deploy and configure HAProxy on Ubuntu servers. It includes all necessary roles, tasks, and templates to ensure a smooth installation and setup process.

## Project Structure

```
ansible-haproxy-deploy
├── playbooks
│   └── haproxy-deploy.yml       # Main playbook for deploying HAProxy
├── roles
│   └── haproxy
│       ├── tasks
│       │   └── main.yml          # Tasks for installing and configuring HAProxy
│       ├── templates
│       │   └── haproxy.cfg.j2    # Jinja2 template for HAProxy configuration
│       └── defaults
│           └── main.yml          # Default variables for HAProxy role
├── inventory
│   └── hosts.ini                 # Inventory file listing target servers
└── README.md                     # Project documentation
```

## Prerequisites

- Ansible installed on your control machine.
- Access to the target Ubuntu servers with sudo privileges.
- Python and the `apt` package manager available on the target servers.

## How to Run the Playbook

1. Clone this repository to your local machine.
2. Navigate to the project directory:
   ```
   cd ansible-haproxy-deploy
   ```
3. Update the `inventory/hosts.ini` file with your target server details.
4. Run the playbook using the following command:
   ```
   ansible-playbook playbooks/haproxy-deploy.yml -i inventory/hosts.ini
   ```

## Customization

You can customize the HAProxy configuration by modifying the `roles/haproxy/defaults/main.yml` file or by passing variables directly in the playbook command.

## License

This project is licensed under the MIT License.