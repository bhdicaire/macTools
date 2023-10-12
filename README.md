![macSetup logo](https://github.com/bhdicaire/macSetup/raw/master/doc/logo.png)

# Ansible-Collection – macTools

This collection includes Ansible roles for macOS automation. For a good example of the collection's usage, refer to my [MacSetup playbook](https://github.com/bhdicaire/macSetup).

Roles included in this collection (click on the link to see the role's README and documentation):

  - `bhdicaire.mac.admin` ([documentation](https://github.com/bhdicaire//macTools/blob/master/roles/admin/README.md))
  - `bhdicaire.mac.chezmoi` ([documentation](https://github.com/bhdicaire/macTools/blob/master/roles/chezmoi/README.md))
  - `bhdicaire.mac.dock` ([documentation](https://github.com/bhdicaire//macTools/blob/master/roles/dock/README.md))

## Installation

Install via Ansible Galaxy:

```
ansible-galaxy collection install bhdicaire.mac
```

Or include this collection in your playbook's `requirements.yml` file:

```
---
collections:
  - name: bhdicaire.mac
```

### Role Requirements

There is no requirements :).
```

## Usage

Here's an example playbook which installs some Mac Apps (assuming you are signed into the App Store), CLI tools via Homebrew, and Cask Apps using Homebrew:

```yaml
- hosts: localhost
  connection: local
  gather_facts: false

  vars:
    mas_installed_app_ids:
      - 424389933 # Final Cut Pro
      - 497799835 # Xcode

    homebrew_installed_packages:
      - node
      - nvm
      - redis
      - ssh-copy-id
      - pv

    homebrew_cask_apps:
      - docker
      - firefox
      - google-chrome
      - vlc

  roles:
    - bhdicaire.mac.homebrew
    - bhdicaire.mac.mas
```

For a real-world usage example, see my [macSetup playbook](https://github.com/bhdicaire/macSetup).

See the full documentation for each role in the role's README, linked above.

## License

MIT

## Author

This collection was created by [Benoît H. Dicaire](https://BHDicaire.com).
