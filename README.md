# Ansible role: SSH

Install and configure server and client SSH.

Only tested on Archlinux.

## Usage
Override [defaults](https://github.com/lunics/ansible_role_ssh/blob/main/defaults/main.yml)
```yaml
ssh_user:
  - owner: foo

ssh_keys_authorized_keys:
  - owner: foo
    state: present
    src:   "{{ path_play }}/files/ssh/key-3.pub"

ssh_keys_generate_keys:
  - path:    "{{ path_play }}/files/ssh/key-1"
    owner:   foo
    type:    ed25519
    comment: foo@laptop-qwert
  - path:    "{{ path_play }}/files/ssh/key-2"
    owner:   foo
    type:    ed25519
    comment: foo@laptop-qwert

ssh_client_config:
  - host:  server-xyz
    owner: foo
    user:  root
    private_key: id_rsa
  - host:  raspberry
    owner: foo
    user:  foo
    private_key: foo-key

ssh_keys_private_keys:
  - owner: foo
    src:   "{{ path_play }}/files/ssh/id_rsa"
  - owner: foo
    src:   "{{ path_play }}/files/ssh/foo-key"
```
TODO
- auto populate private keys needed by ssh_client_config
- replace ssh_keys_generate_keys.path by ssh_keys_generate_keys.dest
