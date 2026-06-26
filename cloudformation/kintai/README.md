# Kintai AWS Infrastructure

この配下は kintai アプリ専用の AWS インフラ定義を置く場所です。

構成:

- `dev/`: 開発環境用テンプレート
- `prd/`: 本番環境用テンプレート

想定対象:

- ECR
- ECS cluster / service / task definition
- RDS PostgreSQL
- S3 template bucket
- CodeBuild / CodePipeline
- 環境別パラメータ