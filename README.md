# born2beroot
## windows11環境での作業の進め方
### 常にrootとして作業する
```
su -
[password]
```
### group関連
1. グループの作成  
```
sudo groupadd user42
```
2. ユーザーをグループに所属させる
```
sudo usermod -aG user42 [name]
```
複数いっぺんに所属させる場合、','を使用して区切る  
```
sudo usermod -aG user42,sudo [name]
```
3. グループに所属しいるのかの確認
userが所属しているgroupを確認する  
```
id [name]
```
groupに所属しているuserを確認する  
```
getent group [group_name]
```
3. オプションについて
'a'オプションは追加、'G'オプションはグループの指定を意味する  
### password関連  
#### password policy について
1. 30日ごとに変更される
1. 変更までに許可される最小期間は2日
1. 有効期限7日前に警告する
1. パスワードが10文字以上
1. パスワードに大文字・小文字・数字を含んでいる
1. ユーザー名が含まれてはいけない
1. 以前のパスワードと7文字以上は違うこと
#### password policy変更方法
##### common-passwordに関する内容
'etc/pam.d/common-password'を編集する(vim,nano,emax)  
common-passwordに含まれる  
```
password	requisite	pam_pwquality.so retry=3
```
に以下の内容を追加する  
```
minlen=10 lcerdit=-1 ucerdit=-1 dcerdit=-1 maxrepeat=2 usercheck=1 difok=7 enforce_for_root
```
##### login.defsに関する変更
'etc/login.defs'を編集する
以下の場所を探す  
```
PASS_MAX_DAYS 99999
PASS_MIN_DAYS 0
PASS_WARN_AGE 7
```
これを以下のように変更する  
```
PASS_MAX_DAYS 30
PASS_MIN_DAYS 2
PASS_WARN_AGE 7
```
## windows11環境の注意すべきコマンド
### reboot
通常のLinux環境ではrebootコマンドを使用して再起動を行うが、windows環境ではrebootコマンドは使用できない  
代わりに(sudo) system reboot を使用する  
### service
これは基本的にsystemコマンドで代用できる  
### ufw
ufwコマンドがnot found表示される際には
```
sudo apt update
sudo apt install ufw
```
というコマンドを使用してインストールを行う  
## 使えそうなリンク
1. [Debian 環境構築メモ](https://love-log.notion.site/Debian-42-9cc59caf0211429aa01e7f52332009ea)
2. [上記サイトの元ネタ](https://baigal.medium.com/born2beroot-e6e26dfb50ac)
3. [youtube](https://www.youtube.com/watch?v=OQEdjt38ZJA)
4. [レビュー用資料](https://discord.com/channels/1064448142457708575/1080548187439370371/1126482456409804811)
