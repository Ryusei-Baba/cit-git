## このリポジトリについて
大学の Wi-Fi で git clone や git push できるようにするための手順（備忘録）です．</br>
一番下のその他の設定が必要になります．</br>
(2022/11/29 現在)

***
## STEP0 準備（一度やれば良い）
```
$ cd
$ ssh-keygen
```
ssh-keygen コマンド実行後，いろいろ聞かれるがすべて Enter を押す．

***
## STEP1
.ssh の中身を確認する．
```
$ cd ~/.ssh/
$ ls
id_rsa  id_rsa.pub  known_hosts
```
中身を確認したら config ファイルを作る．
```
(cd ~/.ssh/)
$ mkdir config
$ ls
config id_rsa  id_rsa.pub  known_hosts
```

***
## STEP2
config ファイルを立ち上げ，以下のコードをコピペして貼り付ける．（人によっては，id_rsa の部分を変える必要がある．）
```
$ vim config
```
```
Host github.com
    Hostname ssh.github.com
    User git
    Port 443
    IdentityFile ~/.ssh/id_rsa
```
保存したら設定は終了．</br>
適当に git clone や git push をしてみる．

***
## その他の設定
GitHub への鍵の登録をする方法．</br>
STEP0 完了後．．．
```
$ cd ~/.ssh/
$ ls
id_rsa  id_rsa.pub  known_hosts
$ cat id_rsa.pub
```
</br>
1. cat id_rsa.pub で出てきた文字をすべてコピーする．</br>
2．コピーしたものを以下の手順で保存する．</br>
GitHub にログイン → 右上のアイコンをクリック → settings を選択 → SSH and GPG keys を選択 → 緑の New SSH key をクリック → Title を適当に決め，Key のところに貼り付ける． → Add SSH key
