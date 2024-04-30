# System Monitor Ansible Playbook'u

Bu Ansible playbook'u, belirli sunucular grubundan CPU kullanımı, RAM kullanımı, disk kullanımı ve sistem çalışma süresi gibi temel sistem metriklerini toplar ve bu bilgileri Markdown formatında bir rapor dosyasına yazar. Bu belge, playbook'un ne yaptığını ve genel amacını açıklamaktadır.

## Özellikler

- **CPU Kullanımı**: Sunucuların CPU kullanım yüzdesini alır.
- **RAM Kullanımı**: Kullanılan RAM miktarını insan-okunabilir biçimde (örneğin, MiB, GiB) elde eder.
- **Disk Kullanımı**: Kök bölümün disk kullanım yüzdesini çeker.
- **Sistem Çalışma Süresi**: Sistemin son yeniden başlatıldığı zamandan beri ne kadar süredir çalıştığını bildirir.

## Önkoşullar

- **SSH** erişimi olan  yetkisine sahip Linux tabanlı hedef sunucular.
````bash
ssh-copy-id -i ~/.ssh/mykey user@192.168.1.152
ssh-copy-id -i ~/.ssh/mykey user@192.168.1.153
ssh-copy-id -i ~/.ssh/mykey user@192.168.1.156
````

## Kullanım

1. **Envanterinizi Yapılandırın**
   `inventory` klasöründeki envanter dosyanızın, metriklerini toplamak istediğiniz sunucuları güncel olarak içerdiğinden emin olun. İşte envanter dosyası için bir örnek yapı:

````yml
all:
  children:
    hypervisor:
      hosts:
        proxmox:
          ansible_host: 192.168.1.152
        hyper-v:
          ansible_host: 192.168.1.152
    storage_server:
      hosts:
        storage1:
          ansible_host: 192.168.1.153
        storage2:
          ansible_host: 192.168.1.156
    web_server:
      hosts:
        web1:
          ansible_host: 192.168.1.153
        web2:
          ansible_host: 192.168.1.156
````


2. **Playbook'u Çalıştır**: Aşağıdaki komut ile Ansible playbook'unu çalıştırın:

```bash
ansible-playbook -i inventory/cluster_inventory.yml site.yml
```

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
├── output
│   └── example.md
├── playbooks
│   └── roles
│       └── system_monitor
│           ├── files
│           ├── handlers
│           ├── meta
│           ├── output
│           ├── tasks
│           │   ├── 01_system_check.yml
│           │   └── main.yml
│           ├── templates
│           └── vars
│               └── main.yml
├── README.md
└── site.yml

13 directories, 11 files
```
