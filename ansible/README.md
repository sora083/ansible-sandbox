### commands

syntax check
```
ansible-playbook -i ./hosts -l web ./playbook.yml --syntax-check
```

test run
```
ansible-playbook -i ./hosts -l web ./install-pkg.yml --check --diff

ansible-playbook -i ./hosts -l web1 ./deploy-middleware.yml --check --diff

ansible-playbook -i ./hosts -l web1 ./01-qualifier.yml --check --diff
```

run
```
ansible-playbook -i ./hosts -l web ./install-pkg.yml

ansible-playbook -i ./hosts -l web1 ./deploy-middleware.yml

ansible-playbook -i ./hosts -l web1 ./01-qualifier.yml
```

slack send
```
ansible-playbook -i ./hosts -l local ./send-slack.yml
```

補足
* ssh_configを設定済み

設定しない場合↓のような記述が必要

```
controller ansible_ssh_user=vagrant ansible_ssh_private_key_file=.vagrant/machines/controller/virtualbox/private_key
target ansible_ssh_user=vagrant ansible_ssh_private_key_file=/.vagrant/machines/target/virtualbox/private_key
```

グループの関係を確認するコマンド
```
ansible-inventory -i hosts --graph
```

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
* nginxのリスタートをどうやるか？ -> templateモジュールではhandlerが使えない
* mysqlは自分でインストールしないほうがいいかも・・

### 参考
* [slack通知](https://qiita.com/imunew/items/ea2bba8859bc709ffa1f)
* [Ansible Slack module をラップして使う](https://qiita.com/yyoshiki41/items/29aab57f44de1d82edc3)