# born2beroot
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
