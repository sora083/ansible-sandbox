### commands

test run
```
ansible-playbook -i ./hosts -l web ./install-pkg.yml --check --diff
ansible-playbook -i ./hosts -l web1 ./deploy-middleware.yml --check --diff

ansible-playbook -i ./hosts -l web1 ./deploy-nginx.yml --check --diff
ansible-playbook -i ./hosts -l web1 ./deploy-mysql.yml --check --diff
ansible-playbook -i ./hosts -l web ./deploy-netdata.yml --check --diff
```

run
```
ansible-playbook -i ./hosts -l web ./install-pkg.yml

ansible-playbook -i ./hosts -l web1 ./deploy-middleware.yml

ansible-playbook -i ./hosts -l web1 ./deploy-nginx.yml
ansible-playbook -i ./hosts -l web1 ./deploy-mysql.yml
ansible-playbook -i ./hosts -l web ./deploy-netdata.yml
```

slack send
```
ansible-playbook -i ./hosts -l local ./send-slack.yml
```

補足
* ssh_configを設定済み

グループの関係を確認するコマンド
```
ansible-inventory -i hosts --graph
```

ファイル説明
* install-pkg
    * 初期インストール
* deploy-middleware
    * nginx
    * mysql
    * netdata

### サービスの確認
```
service --status-all | grep -E "mysql|nginx|netdata"
```


### 課題
* slack通知の連携が出来ていないので改善が必要
* mysqlは自分でインストールしないほうがいいかも・・
* データの初期化タスクをmysqlで入れられないか？

### 参考
* [slack通知](https://qiita.com/imunew/items/ea2bba8859bc709ffa1f)
* [Ansible Slack module をラップして使う](https://qiita.com/yyoshiki41/items/29aab57f44de1d82edc3)