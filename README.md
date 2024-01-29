# Ansible role: SSH

Install and configure server and client SSH.

Only tested on Archlinux.

## Usage
Override [defaults](https://github.com/lunics/ansible_role_ssh/blob/main/defaults/main.yml)
```yaml
user:
  - name:  foo
    group: wheel
    ssh:   "{{ ssh_foo }}"

ssh_foo:
  config:
    - host:        laptop-1
      user:        foo
      private_key: key_laptop-1
    - host:        desktop-10
      user:        bar
      private_key: key_laptop-10
  authorized_keys:
    - "{{ path_play }}/files/ssh/key_laptop-1.pub"
  private_keys:
    - "{{ path_play }}/files/ssh/key_laptop-1",
    - "{{ path_play }}/files/ssh/key_laptop-10"
```
## TODO
- know_hosts.yml
- generated_keys.yml
- add inspired from repos
- encrypt private keys with vault and check copy module using and working
- replace ssh_keys_generate_keys.path by ssh_keys_generate_keys.dest
- change all vars/main.yml like sshd.config.path by sshd_confing_path ?
