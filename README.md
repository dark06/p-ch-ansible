# PCH Ansible

## Development Environment

- macOS

## Pre-requisites

- [Python](https://www.python.org/downloads/) `v3.12.7`
- [Task](https://taskfile.dev/) `v3.42.1`

> [!IMPORTANT]
> Create a `.env` file in the root directory of the project and add the required environment variables as shown in the `.env.tpl` file.

## Solution

- Ansible manages the entire setup process, from ensuring that openssh-server is installed to installing Go, which is required for executing the program that monitors the Nginx container’s health.
Additionally, it adds the generated SSH key to the authorized_keys file of the remote server (restricted to the `ubuntu` user) and finalizes the configuration of the software responsible for health checks on the Nginx container.

- The generated private key is stored in `/home/ubuntu/secrets/id_ed25519`.

- When running the Ansible playbook using the [Task](https://taskfile.dev) `task playbook:run`, a new SSH key is generated and stored locally in the `secrets` directory.

- The Go program for monitoring the health of the Nginx container can be executed by running the `nginx_check` command in the terminal.
