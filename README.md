# 42-matcha

このプロジェクトは、Makeコマンドを使用してDockerコンテナ環境を効率的に管理するためのシステムを提供します。

## はじめに

### 必要条件

- Docker
- Docker Compose
- Make

### インストール手順

1. このリポジトリをクローン
2. プロジェクトディレクトリに移動
3. `make build` を実行して環境を構築

## 使用方法

### アプリケーションへのアクセス

環境の起動後、以下のURLからブラウザでアプリケーションにアクセスできます：

```
https://localhost
```

### 利用可能なコマンド

`make` コマンドだけを実行すると、デフォルトで `make build` が実行されます。

以下のMakeコマンドを使用して、Docker環境を管理できます：

- `make build`: コンテナをビルドし、デタッチドモードで起動後、立ち上げる
- `make up`: コンテナを起動する
- `make down`: コンテナ、ネットワーク、ボリュームを停止および削除する
- `make stop`: 実行中のコンテナを削除せずに停止する
- `make restart`: 実行中のコンテナを再起動する
- `make clean`: すべてのコンテナ、ボリューム、ローカルイメージを停止および削除する
- `make prune`: システム全体のクリーンアップを実行する（注意して使用してください）
- `make re`: サービスを再起動する（downを実行後、buildを実行）
- `make status`: 以下の状態を表示：
  - 実行中のコンテナ
  - Dockerイメージ
  - ボリューム
  - ネットワーク

### 使用例

初回環境構築時：
```bash
make
```
または

```bash
make build
```

全サービスの停止：
```bash
make down
```

Docker リソースの状態確認：
```bash
make status
```

完全なクリーンアップの実行：
```bash
make prune
```

## プロジェクト構成

Docker環境は `./srcs/docker-compose.yml` で定義されています。

## メンテナンス

### 定期的なメンテナンス

Docker環境を清潔で効率的に保つために：

1. `make status` を定期的に実行してリソース使用状況を監視
2. `make clean` を使用して未使用のリソースを削除
3. システム全体のクリーンアップには `make prune` を使用（注意が必要）

### トラブルシューティング

問題が発生した場合：

1. `make status` でコンテナの状態を確認
2. `make re` でサービスの再起動を試みる
3. 問題が解決しない場合は、クリーンビルドを実行：
   ```bash
   make prune
   make build
   ```

## 注意事項

- `make prune` コマンドは、システム全体の未使用Dockerリソースを削除します。注意して使用してください。
- クリーンアップコマンドを実行する前に、作業内容が確実にコミットされていることを確認してください。