# Infra Repository

この `infra` はアプリ本体とは独立した、AWS インフラ定義用のリポジトリです。

現在は CloudFormation ベースで管理しています。

GitHub Actions は `infra` 配下ではなく、workspace 直下の `.github/workflows/` で app と合わせて一元管理します。

## 構成

```text
infra/
└─ cloudformation/
   ├─ common/
   │  ├─ all/
   │  ├─ dev/
   │  └─ prd/
   └─ kintai/
      ├─ dev/
      ├─ prd/
      └─ README.md
```

## 役割

- `cloudformation/common/`: 複数アプリで共有する基盤定義
- `cloudformation/common/all/`: 全環境共通のテンプレート
- `cloudformation/common/dev/`: 開発環境向け共通定義
- `cloudformation/common/prd/`: 本番環境向け共通定義
- `cloudformation/kintai/`: kintai アプリ専用のインフラ定義

## GitHub Actions との関係

- `.github/workflows/ci-gitaction.yml`: `App/kintai` と `infra` の変更をまとめて検知する CI
- `.github/workflows/sync-codecommit.yml`: workspace 全体を CodeCommit に mirror する同期

## 今後の増やし方

将来的にアプリごとのリポジトリを増やす場合も、この `infra` 側にアプリ単位のディレクトリを追加していきます。

例:

- `cloudformation/kintai/`
- `cloudformation/app-b/`
- `cloudformation/app-c/`

共通基盤は `common/` に、アプリ固有の基盤は `cloudformation/<app-name>/` に寄せる方針です。