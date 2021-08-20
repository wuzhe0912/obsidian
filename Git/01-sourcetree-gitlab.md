# SourceTree 連接 GitLab

tags: #Git
links: 目錄 -[[00-git-index]]

雖然這邊記錄的範例是連接`GitLab`，但`GitHub`的操作也基本相同。

## Windows 環境

打開`Terminal`，使用以下指令來產生`SSH Key`:

``` sh
ssh-keygen -t rsa -b 2048 -C "register GitLab mail"
```

建立`rsa`的過程中，會詢問是否設定密碼，可選擇不設。完成後，預設會產生在以下位置:

``` sh
C:\Users\username\.ssh
```

`ssh`檔案底下會有兩個檔案，分別是`id_rsa`、`id_rsa.pub`。

## SourceTree

打開`SourceTree -> Tools -> Options`，可以看到下圖，在`SSH Client`選擇`OpenSSH`，`SSH Key`則選我們剛剛建立的`id_rsa`檔案，最選點選`OK`就完成`SourceTree`連結`GitLab`。

![設定 sourcetree](https://cdn.jsdelivr.net/gh/wuzhe0912/obsidian-image@master/1629435474712.3u1lc9ohsms0.jpg)

## Command Line

如果使用終端機操作指令的方式，而非使用`GUI`工具，則需要將公鑰貼到`GitLab 的 SSH Key`。

打開剛剛建立的`id_rsa.pub`，將內容複製後，回到`GitLab`頁面，點選右上角的`Perferences`，接著選左側的`SSH Keys`，將剛剛複製的內容，貼到中間的空白欄位，建立一個名稱，選擇過期時間，最後點選`Add Key`完成。

![設定 GitLab SSH Key](https://cdn.jsdelivr.net/gh/wuzhe0912/obsidian-image@master/1629444357342.5rt7njysn8w0.jpg)
