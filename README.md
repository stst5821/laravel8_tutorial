参考サイト： 
https://qiita.com/ucan-lab/items/56c9dc3cf2e6762672f4  
  
コンテナ  
nginx 1.18  
php 7.4.16  
composer導入済み 
npm導入済み

npm導入参考サイト：  
https://tsyama.hatenablog.com/entry/docker-not-found-npm

## コンテナの名前を変更する

このテンプレを使ってすでに他のコンテナを作っていた場合、
コンテナ名がかぶって起動できなくなるので、コンテナ名を変更する必要がある。

[変更箇所]

- docker-compose.yml

```
services:
サービス名（app,web,db）を変更する。

※container_name: db　が書かれていると、こちらの名前が優先されてしまうので、
記述そのものを消すか、名前を変更する。
```

- default.conf

```
location ~ \.php$ {
        fastcgi_pass app:9000; // ←ここの「app」をdocker-compose.ymlで変更したappのコンテナ名と同じにする。（app→testAppに変更したなら、こちらもtestAppに変える。）
        fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;
        include fastcgi_params;
    }
```

## コンテナ起動方法

docker-compose up -d
  
## laravel導入
  
docker-compose exec [コンテナ名] bash  
composer create-project --prefer-dist "laravel/laravel=７.*" .  
php artisan -V  // バージョン確認  

composer create-project --prefer-dist "laravel/laravel=７.*" .  
を実行後、エラーになる場合  
  
appコンテナに入り、
`ls -a`
を実行する  
.DS_storeというファイルがあった場合は、  
`find -name ".DS_Store" -delete`  
で削除してから、再度実行すると、インストールできる。  
  
以下のサイトを開き、laravelのトップ画面が開けばOK 
http://localhost:8080/
