# Ansible Playbook for Pop!_OS Setup

# Overview

This Ansible playbook automates the setup of a development environment on Pop!_OS. It installs essential tools, configures system settings, and ensures a smooth developer experience with applications like GitHub CLI, Neovim, Obsidian, and more.


## Pre-Requisites:

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


# Playbook Overview & Structure

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

## Running the playbook

Run the full playbook

```bash
ansible-playbook playbook.yml --ask-become-pass
```

### Run / Skip Tags
Use --tags <tagname> to run specific parts of the playbook. Example:

### Run Specific Tags
```sh
ansible-playbook main.yml --tags github
```

### Skip Specific Tags

```sh
ansible-playbook main.yml --tags programming_languages --skip-tags java
```


## Playbook Structure

```sh
✗ tree
.
├── roles
│   ├── common                   # Tags: ['common']
│   │   └── tasks
│   │       ├── aliases.yml         # Tags: ['aliases']
│   │       ├── apt.yml             # Tags: ['apt']
│   │       ├── bitwarden.yml       # Tags: ['bitwarden']
│   │       ├── chrome.yml          # Tags: ['chrome']
│   │       ├── fonts.yml           # Tags: ['fonts']
│   │       └── main.yml
│   ├── dev_tools               # Tags: ['dev_tools']
│   │   └── tasks
│   │       ├── docker.yml          # Tags: ['docker']
│   │       ├── eza.yml             # Tags: ['eza']
│   │       ├── github.yml          # Tags: ['github']
│   │       ├── insomnia.yml        # Tags: ['insomnia']
│   │       ├── lazydocker.yml      # Tags: ['lazydocker']
│   │       ├── main.yml            
│   │       ├── neovim.yml          # Tags: ['neovim']
│   │       ├── obsidian.yml        # Tags: ['obsidian']
│   │       ├── starship.yml        # Tags: ['starship']
│   │       └── vscode.yml          # Tags: ['vscode']
│   └── programming_languages   # Tags: ['programming_languages']
│       └── tasks
│           ├── go.yml              # Tags: ['go']
│           ├── java.yml            # Tags: ['java']
│           ├── main.yml            
│           ├── npm.yml             # Tags: ['npm']
│           └── python.yml          # Tags: ['python']
└── vars
│    ├── apt_packages.yml       # Packages to be installed with 'apt'
│    ├── bash_aliases.yml       # Aliases to add to .bash_aliases
│    ├── starship_vars.yml      # Configuration file for Starship
│    └── vscode_extensions.yml  # VSCode Extensions to install
├── ansible.cfg
├── config.yml                  # Main config file playbook
├── inventory.cfg
├── main.yml                    # Main Playbook
├── README.md
'''

