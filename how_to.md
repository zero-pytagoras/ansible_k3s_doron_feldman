folder structure, install role:
roles/
├── k3s_install/
│   ├── tasks/
│   │   └── main.yml
│   ├── files/
│   │   └── k3s_binary
│   └── templates/

main.yml:

---
- name: Copy K3s binary
  copy:
    src: k3s_binary
    dest: /usr/local/bin/k3s
    mode: '0755'

- name: Install K3s master
  command: /usr/local/bin/k3s server
  when: inventory_hostname == 'master'

agent role:

roles/
├── k3s_agent/
│   ├── tasks/
│   │   └── main.yml
│   ├── files/
│   │   └── k3s_binary
│   └── templates/


---
- hosts: all
  roles:
    - k3s_install
    - k3s_agent


script to run the playbook:

#!/bin/bash

ansible-playbook -i inventory playbook.yml


chmod +x run_playbook.sh


Notes:
Ensure you have the K3s binary in the files directory of both roles.
Update the inventory file with your master and agent node details.
Read the K3s install script carefully to understand any additional configurations you might need.
Feel free to ask if you need further assistance or have any questions!
