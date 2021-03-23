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
  
以下のサイトを開き、laravelのトップ画面が開けばOK    
http://127.0.0.1:10080/
