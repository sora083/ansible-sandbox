### commands

#### dry-run
```
ansible-playbook -i ./hosts -l web ./install-pkg.yml --check --diff
ansible-playbook -i ./hosts -l web1 ./deploy-middleware.yml --check --diff

ansible-playbook -i ./hosts -l web1 ./deploy-nginx.yml --check --diff
ansible-playbook -i ./hosts -l web1 ./deploy-mysql.yml --check --diff
ansible-playbook -i ./hosts -l web ./deploy-netdata.yml --check --diff
ansible-playbook -i ./hosts -l web ./deploy-systemd.yml --check --diff

ansible-playbook -i ./hosts -l web1 ./deploy-redis.yml --check --diff
```

#### run
```
ansible-playbook -i ./hosts -l web ./install-pkg.yml

ansible-playbook -i ./hosts -l web1 ./deploy-middleware.yml

ansible-playbook -i ./hosts -l web1 ./deploy-nginx.yml
ansible-playbook -i ./hosts -l web1 ./deploy-mysql.yml
ansible-playbook -i ./hosts -l web ./deploy-netdata.yml
ansible-playbook -i ./hosts -l web ./deploy-systemd.yml

ansible-playbook -i ./hosts -l web1 ./deploy-redis.yml
```

### ファイル説明
* install-pkg: パッケージインストール
* deploy-middleware: 各ミドルウェアのタスクを一発実行
    * nginx: nginxのconfファイル配置と再起動
    * mysql: mysqlのconfファイル配置と再起動
    * netdata: netdataのconfファイル配置と再起動

### Tips
#### サービスの確認
```
service --status-all | grep -E "mysql|nginx|netdata"
```

#### グループの関係を確認するコマンド
```
ansible-inventory -i hosts --graph
```
#### slacのwebトークン確認
https://${your domain}.slack.com/apps/manage

### 課題
* redisのインストールうまく行かない・・
* netdataの設定を見直したほうが良いかも
* nginx, mysqlの情報を追加する
* https://github.com/ysokjkr/isucon9_scriptに移す

### 参考
* [slack通知](https://qiita.com/imunew/items/ea2bba8859bc709ffa1f)
* [Ansible Slack module をラップして使う](https://qiita.com/yyoshiki41/items/29aab57f44de1d82edc3)