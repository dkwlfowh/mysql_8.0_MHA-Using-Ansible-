# mysql_8.0_MHA-Using-Ansible-

### 1. Ansible Download


### 2. Ansible.cfg 수정


### 3. /etc/hosts 수정 ( Ansible 서버 ) 
```
vim /etc/ansible/ansible.cfg
[defaults]
host_key_checking = False
```

### 4. ansible hosts 등록 ( Ansible 서버 ) 
```
vim /etc/ansible/hosts
192.168.100.20 master
192.168.100.21 slave
192.168.100.22 manager
```

### 5. git down 
```
git clone https://github.com/dkwlfowh/mysql_8.0_MHA-Using-Ansible-.git
```

### 6. vars/main.yml 변수들 환경에 맞게 수정 ( ex, DB Server IP / DB 설치 파일 )

**DB 설치 파일이 templates/ 디렉토리에 업로드 해주어야된다.**
```
vim /etc/ansible/roles/mysql/vars/main.yml
---
# vars file for maria
mysql_root_password: root
mysql_user: repl
mysql_user_password: repl
datadir: /data/data
logdir: /data/log
master: 192.168.100.20
slave: 192.168.100.21
dbfile: mysql-commercial-8.0.22-el7-x86_64

[root@monitoring templates]# ll
total 1004300
-rw-r--r-- 1 root root        474 Mar 15  2022 manager_bash.txt
-rw-r--r-- 1 root root        806 Sep 20 15:54 master.cnf
-rw-r--r-- 1 root root       3924 Mar 17  2022 master_ip_failover
-rw-r--r-- 1 root root      10151 Mar 17  2022 master_ip_online_change
-rw-r--r-- 1 root root        162 Mar 16  2022 master_vip_up.sh
-rw-r--r-- 1 root root     118521 Mar 15  2022 mha4mysql-manager-0.57.tar.gz
-rw-r--r-- 1 root root      54484 Mar 15  2022 mha4mysql-node-0.57.tar.gz
-rw-r--r-- 1 root root        891 Mar 15  2022 mha.cnf
-rw-r--r-- 1 root root 1028174416 Sep 20 11:13 mysql-commercial-8.0.22-el7-x86_64.tar.gz
-rw-r--r-- 1 root root        314 Sep 20 13:13 mysql.service
-rw-r--r-- 1 root root        806 Sep 21 11:16 slave.cnf
-rw-r--r-- 1 root root        162 Mar 16  2022 slave_vip_up.sh
-rw-r--r-- 1 root root       1180 Mar 16  2022 ssh.txt
```

### 7. Key YML 파일 실행
```
cd /etc/ansible/roles/mysql
ansible-playbook key.yml -k
SSH password:
```
### 8. INSTALL_DB.YML 파일 
```
ansible-playbook /etc/ansible/roles/mysql/install_db.yml
```
