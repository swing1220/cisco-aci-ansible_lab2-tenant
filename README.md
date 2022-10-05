# Lab2 - 논리구성 작업

#### Case 1

- Task 확인

```
ansible-playbook tenant.yml --list-tasks
```

#### Case 2

- Dry-Run 및 작업 수행

```
ansible-playbook tenant.yml --check
ansible-playbook tenant.yml
```

#### Case 3

- Bridge Domain 추가

```yaml
bridge_domains:
  - { name: "COMPUTE2_SVC", vrf: "DEMO" }

subnets:
  - { bd: "COMPUTE2_SVC", vrf: "DEMO", subnet: "10.10.13.1/24", scope: "public" }
```

```
ansible-playbook tenant.yml --tags bd --skip-tags epg --check
ansible-playbook tenant.yml --tags bd --skip-tags epg
```

#### Case 4

- Bridge Domain 삭제

```yaml
bridge_domains:
  - { name: "COMPUTE2_SVC", vrf: "DEMO", state: "absent" }
```

```
ansible-playbook tenant.yml --tags bd --skip-tags epg --check
ansible-playbook tenant.yml --tags bd --skip-tags epg
```
