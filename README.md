参考サイト： 
https://qiita.com/ucan-lab/items/56c9dc3cf2e6762672f4  
  
コンテナ  
nginx 1.18  
php 7.4.16  
composer導入済み  
  
あとは以下の流れで好きなlaravelのverを入れればOK
  
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
http://127.0.0.1:10080/
