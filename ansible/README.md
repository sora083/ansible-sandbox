### commands

syntax check
```
ansible-playbook -i ./hosts -l web ./playbook.yml --syntax-check
```

test run
```
ansible-playbook -i ./hosts -l web ./00-devel.yml --check --diff

ansible-playbook -i ./hosts -l web ./01-qualifier.yml --check --diff

ansible-playbook -i ./hosts -l web1 ./01-qualifier.yml --check --diff
```

test command
```
ansible -i hosts all -m ping
```

run
```
ansible-playbook -i ./hosts -l web ./00-devel.yml
```

try
```
ansible-playbook -i ./hosts -l web1 ./01-qualifier.yml

ansible-playbook -i ./hosts -l local ./send-slack.yml
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
    * nginx
    * mysql
    * netdata

### サービスの確認
```
service --status-all | grep -E "mysql|nginx|netdata"
```


### 課題
* 変数差し替えができていない
* nginxのリスタートでエラー -> たぶん変数差し替えがうまくいったないせい
* mysqlは自分でインストールしないほうがいいかも・・

### 参考
* [slack通知](https://qiita.com/imunew/items/ea2bba8859bc709ffa1f)
* [Ansible Slack module をラップして使う](https://qiita.com/yyoshiki41/items/29aab57f44de1d82edc3)