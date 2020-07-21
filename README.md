# RaspberryPI First Initial Setup

## python 環境安裝
本程式使用 _Ansible_ 工具做為佈署工具，兩種方式擇一安裝即可

1. 使用 Pipenv
    ```
    $ pipenv install ansible
    ```

2. 使用 pip
   ```
   $ pip install ansible
   ```
## sshpass 安裝

- ubuntu
    ```shell
    $ sudo apt install sshpass
    ```

- CentOS
    ```
    $ yum install sshpass
    ```

## 佈署

1. 修改主機位置檔 _hosts_

    ```vim
    [piserver]
    pi1 ansible_host=192.168.55.110 ansible_user=maxron ansible_ssh_pass=a12345 ansible_sudo_pass=a12345 ansible_port=22

    ```
    
    **設定檔解說**
    - piserver: 主機別名，可設定任意名稱
    - ansible_host: 目標主機 IP
    - ansible_user: 目標主機使用者
    - ansible_ssh_pass: 目標主機密碼
    - ansible_sudo_pass: 目標主機具有 _sudo_ 權限的密碼
    - ansible_port: ssh port
  
    可設定多台主機，每台主機的配置不可分行，範例如下:

    ```vim
    [dbserver]
    server1 ansible_host=192.168.55.110 ansible_user=maxron ansible_ssh_pass=a12345 ansible_sudo_pass=a12345 ansible_port=22
    db01 ansible_host=192.168.55.120 ansible_user=maxron ansible_ssh_pass=a12345 ansible_sudo_pass=a12345 ansible_port=22
    ```

2. 執行佈署

    _hosts_ 設定檔修改完成後，使用以下指令佈署
   
   ```bash
   $ ansible-playbook first-setup.yaml
   ```
