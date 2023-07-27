### 環境を構築する
- Docker 環境構築
  ```shell
  $ cd ~/test_laravel
  $ docker compose up -d
  $ docker compose exec php chmod -R 777 .
  ```
- Laravel 環境構築
  ```shell
  $ docker compose exec php cp .env.local .env
  $ docker compose exec php composer install
  $ docker compose exec php php artisan key:generate
  $ docker compose exec php php artisan storage:link
  $ docker compose exec php php artisan migrate
  ```

- envファイル
  ```dotenv
  DB_CONNECTION=mysql
  DB_HOST=db
  DB_PORT=3306
  DB_DATABASE=database
  DB_USERNAME=laravel
  DB_PASSWORD=password
  ```

- Docker を起動
  ```shell
  $ docker compose up -d 
  ```

- 一度停止させる
  ```shell
  $ docker compose down
  ```

- キャッシュクリア
  ```shell
  $ docker compose exec php php artisan cache:clear
  $ docker compose exec php php artisan config:clear
  $ docker compose exec php php artisan route:clear
  $ docker compose exec php php artisan view:clear
  $ docker compose exec php composer dump-autoload
  ```

### メモ
- Docker キャッシュクリアしつつインスタンスを停止
  ```shell
  $ docker compose down --rmi all --volumes --remove-orphans
  ```
