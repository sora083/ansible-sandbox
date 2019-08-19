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

### ssh-copy-id
```
ssh-copy-id -i ~/isucon/.ssh/id_rsa.pub isucon@${target_host}
```

### 懸念点
* ssh-addとかで秘密鍵の登録が必要？
* ssh-copy-idで全て追記になる？