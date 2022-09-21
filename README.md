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


### 6. vars/main.yml 변수들 환경에 맞게 수정 ( ex, DB Server IP / DB 설치 파일 )

*DB 설치 파일이 templates/ 디렉토리에 업로드 해주어야된다.


### 7. Key YML 파일 실행


### 8. INSTALL_DB.YML 파일 
