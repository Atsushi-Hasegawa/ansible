# Ansible Playbooks for Infrastructure

This repository contains Ansible playbooks and roles for managing infrastructure, specifically targeting AWS environments.

## Prerequisites

- **Ansible**: 2.9 or later
- **Python Libraries**: `boto3` and `botocore` (required for the AWS EC2 inventory plugin)
- **AWS CLI**: Configured with appropriate credentials and access to the `ap-northeast-1` region.

## Configuration

The project settings are defined in `ansible.cfg`. Key configurations include:

- **Inventory**: Uses `aws_ec2.yml` (AWS Dynamic Inventory).
- **Remote User**: `terraform-user`
- **Private Key**: `~/.ssh/id_rsa`
- **Host Key Checking**: Enabled

The `aws_ec2.yml` file filters for running instances in the `ap-northeast-1` region and groups them based on their `Name`, `Role`, and `Group` tags.

## Usage

### Running the Main Playbook

To apply the configuration to your AWS instances:

```bash
ansible-playbook site.yml
```

### Local Testing

To run the playbooks against a local environment (e.g., localhost), you can use the provided test inventory files:

```bash
ansible-playbook -i test_hosts site.yml
```

## Playbooks

- `site.yml`: The master playbook that imports `operation.yml`.
- `operation.yml`: Defines the roles to be applied to the `operation` host group.

## Available Roles

| Role | Description |
| :--- | :--- |
| `common` | Basic system hardening and common utilities (e.g., history hardening, basic iptables). |
| `elasticsearch` | Installs and configures Elasticsearch. |
| `fluentd` | Installs and configures Fluentd for log aggregation. |
| `gitlab` | Installs and configures GitLab. |
| `httpd` | Installs and configures Apache HTTP Server. |
| `iptables` | Manages firewall rules. |
| `java` | Installs Java (OpenJDK). |
| `kibana` | Installs and configures Kibana for data visualization. |
| `mongodb` | Installs and configures MongoDB. |
| `mysql` | Installs and configures MySQL Server. |
| `npm` | Installs Node.js and npm. |
| `php` | Installs PHP. |
| `postfix` | Installs and configures Postfix for mail services. |
| `python` | Installs and configures Python environment. |
| `ruby` | Installs Ruby environment. |

## License

This project is for internal use. Please refer to the repository owner for licensing details.
