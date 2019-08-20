# ssh設定
### ssh鍵生成
```
mkdir -p ~/isucon/.ssh
ssh-keygen -t rsa -f ~/isucon/.ssh/id_rsa
```

### 生成された鍵の確認
```
ls -l ~/isucon/.ssh
```

### 公開鍵をセット
```
cat ~/isucon/.ssh/id_rsa.pub| ssh isucon@${target_host} "mkdir -p ~/.ssh; cat >> ~/.ssh/authorized_keys"

e.g.)
cat ~/isucon/.ssh/id_rsa.pub| ssh vagrant@controller "mkdir -p ~/.ssh; cat >> ~/.ssh/authorized_keys"
cat ~/isucon/.ssh/id_rsa.pub| ssh vagrant@target "mkdir -p ~/.ssh; cat >> ~/.ssh/authorized_keys"
```

### 懸念点
* ssh-addとかで秘密鍵の登録が必要？
* ssh-copy-idで全て追記になる？