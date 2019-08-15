
syntax check
```
ansible-playbook -i ./hosts ./playbook.yml --syntax-check
```

test run
```
ansible-playbook -i ./hosts ./00-devel.yml --check --diff
```

test command
```
ansible -i hosts all -m ping
```

run
```
ansible-playbook -i ./hosts ./00-devel.yml
```

補足
* ssh_configを設定済み

設定しない場合↓のような記述が必要

```
controller ansible_ssh_user=vagrant ansible_ssh_private_key_file=.vagrant/machines/controller/virtualbox/private_key
target ansible_ssh_user=vagrant ansible_ssh_private_key_file=/.vagrant/machines/target/virtualbox/private_key
````

ファイル説明
* 00-devel
    * 初期インストール
* 01-qualify
    * nginx, mysql