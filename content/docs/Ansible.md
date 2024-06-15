---
title: Ansible
type: docs
prev: docs/
next: docs/Bash
---

## Running `ansible-playbook`
* Limit to host/group: `--limit "host,group"`
* Run with specific variables: `--extra-vars "key=value"` | `--extra-vars "my_array=['item1','item2']"`
* Run as different user: `-u <username>`
* Prompt for pass and sudo: `-kK`

## Ad-hoc
Get date/time for all hosts:
```sh
ansible all -a "date"
```

## Tasks
### With Items / Loops
Loop through a defined host group (`with_items` can be substituted in for `loop`, but is legacy):
```yml
loop: "{{ groups['host_group'] }}"
```

### When
Only run on certain host groups: `when: inventory_hostname in lookup('inventory_hostnames', 'BSs:BMs')`

### `lineinfile`
#### Adding host to `/etc/hosts`
```yml
- name: Add host to /etc/hosts
    lineinfile:
      path: /etc/hosts
      state: present
      owner: root
      group: adm
      mode: 0644
      regexp: '^"{{ ip }}" ip.example.com'
      line: '{{ ip }} ip.example.com'
```
#### Adding a sudoers file
```yml
- name: Add admin to sudoers
  lineinfile:
    create: yes
    state: present
    owner: root
    group: root
    mode: 0600
    dest: "/etc/sudoers.d/admin"
    regexp: "admin  ALL=NOPASSWD: /bin/cp *"
    line: "admin  ALL=NOPASSWD: /bin/cp *"
    validate: /usr/sbin/visudo -cf %s
```

## Roles
### Template role
```yml {filename="roles/logger/tasks/main.yml"}
- name: Template task
  template:
    src: source.j2
    dest: "{{ logger.path }}"
  when: logger is defined
  tags: log-tag
```

```yml {filename="roles/other_role/tasks/main.yml"}
- name: Configure logger
  include_role:
    name: logger
    apply:
      tags: log-tag
  vars:
  logger:
    path: /my/path
```

## Handlers
```yml
- name: Flush handlers
  meta: flush_handlers
```
