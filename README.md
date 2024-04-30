## To do

# Yapı

```bash
ansible-role-system-monitor/
├── ansible.cfg
├── collections
│   └── requirements.yml
├── hosts
├── inventory
│   └── server_groups.yml
├── LICENSE
├── playbooks
│   └── roles
│       └── system_monitor
│           ├── files
│           ├── handlers
│           ├── meta
│           ├── tasks
│           │   ├── 01_check_cpu.yml
│           │   ├── 02_check_ram.yml
│           │   ├── 03_check_disk.yml
│           │   ├── 04_check_uptime.yml
│           │   ├── 05_output.yml
│           │   └── main.yml
│           ├── templates
│           └── vars
│               └── main.yml
├── README.md
└── site.yml

11 directories, 14 files
```
