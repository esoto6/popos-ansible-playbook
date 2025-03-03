# Ansible Playbook for Pop!_OS Setup

# Overview

This Ansible playbook automates the setup of a development environment on Pop!_OS. It installs essential tools, configures system settings, and ensures a smooth developer experience with applications like GitHub CLI, Neovim, Obsidian, and more.


# Pre-Requisites:

1. System has been updated
    ```sh
    sudo apt-get update && sudo apt-get upgrade -y
    ```
2. Install Ansible
    ```sh
    sudo apt install python3-pip
    pip install --user ansible
    export PATH=$PATH:~/.local/bin
    ```


# Playbook Structure

## Roles and Tasks Overview

Each role contains specific tasks catgegorized under common tags. This allowis you to selectively run parts of the playbook depending on your requirements.

### Role: common
Installs common tooling configurations and options such as:
- Setting up bash aliases for Git, Docker and general commands
- Ensuring essential packages are installed.

### Role: dev_tools
Installs developer related tools suchs as:
- Github CLI(gh)
- Neovim(nvim)
- Docker

### Role: programming_languages
Install programming languages such as:
- Python
- Java
- Node
- Go

### Tags Overview

To see all avilable tags you can run the below command
```sh
ansible-playbook main.yml --list-tasks
```

# Running the playbook

Run the full playbook

```sh
ansible-playbook playbook.yml --ask-become-pass
```

# Run / Skip Tags
Use --tags <tagname> to run specific parts of the playbook. Example:

## Run Specific Tags
```sh
ansible-playbook main.yml --tags github
```

## Skip Specific Tags

```sh
ansible-playbook main.yml --tags programming_languages --skip-tags java
```