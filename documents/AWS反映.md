# AWS 反映

## 設定ファイル変更

- ファイルパス

```
app/vue.config.js
```

- 追記

```
module.exports = {
  configureWebpack: {
  },
  lintOnSave: false, // これを追記
  pwa: {
  },
  css: {
  },
};

```

## ビルド

- ビルド

```
app$ npm run build

DONE  Build complete. The dist directory is ready to be deployed.
```

- フォルダ確認

```
app % ls -1

dist
vue.config.js
```

## AWS でディレクトリ作成

```
sudo mkdir -p /var/www/portfolio
sudo chown -R $USER:$USER /var/www/portfolio
```

## ローカル dist を EC2 に転送

- ssh ディレクトリに移動

```
% cd ~/.ssh
```

- bash

```
#!/bin/bash

# 変数定義
KEY="iam-key-001.pem"
USER="ubuntu"
HOST="ec2-11-111-1-111.ap-southeast-2.compute.amazonaws.com"
LOCAL_DIR="/Users/developer/Desktop/work/portfolioArgonVueApp/app/dist"
REMOTE_DIR="/var/www/portfolio"

# SCP 実行（dist 配下の中身だけコピー）
scp -i "$KEY" -r "$LOCAL_DIR"/* "$USER@$HOST:$REMOTE_DIR"

```

## サーバーブロックファイル作成

- ファイル編集

```
sudo nano /etc/nginx/sites-available/portfolio
```

- ファイル内容

```
server {
    listen 80;
    server_name domain.com www.domain.com;

    root /var/www/portfolio;
    index index.html index.htm;

    location / {
        try_files $uri $uri/ /index.html;
    }
}

```

## 設定確認と再起動

```
sudo nginx -t
sudo systemctl restart nginx
```

## HTTP が動く状態で Certbot を実行

「1」を入力.

```
$ sudo certbot --nginx -d domain.com

What would you like to do?
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
1: Attempt to reinstall this existing certificate
2: Renew & replace the certificate (may be subject to CA rate limits)
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Select the appropriate number [1-2] then [enter] (press 'c' to cancel): 1


Deploying certificate
Successfully deployed certificate for travel600.website to /etc/nginx/sites-enabled/portfolio
Congratulations! You have successfully enabled HTTPS on https://travel600.website

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
If you like Certbot, please consider supporting our work by:
 * Donating to ISRG / Let's Encrypt:   https://letsencrypt.org/donate
 * Donating to EFF:                    https://eff.org/donate-le
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
```

## 所有者と権限を調整（Nginx が読めるように）

```
sudo chown -R www-data:www-data /var/www/portfolio
sudo chmod -R 755 /var/www/portfolio
```

## 完了後に確認

```
$ sudo nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful

sudo systemctl restart nginx
```
