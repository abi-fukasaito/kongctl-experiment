# kongctl-experiment

ブログ記事「[kongctlの基本的な使い方](https://qiita.com/fukafukaCat/items/fa0f628da148232cc460)」で作成したコードを保存しているリポジトリです。
## 概要

- kongctl を使って、設定内容の異なる複数の Control Plane（CP）を管理できます。
- 各 CP で共通する設定を `common.yml` に切り出し、CP ごとの差分だけを個別ファイルで管理できます

## 今回の環境
- decK 1.69.0
- kongctl 1.21.0
- Kong Konnect
- Ubuntu 24.04.5(WSL)

## フォルダ構成

```
.
├ gateway/            # CP内設定
│　└ common.yml       # 共通設定
│　└ cp1.yml          # CP1用設定
│　└ cp2.yml          # CP2用設定
├ platform_cp1.yml    # CP1作成用
└ platform_cp2.yml    # CP2作成用
```

## 各ファイルの役割

| ファイル                 | 役割                   |
| -------------------- | -------------------- |
| `platform_cp1.yml`   | CP1 そのものを作成するための設定   |
| `platform_cp2.yml`   | CP2 そのものを作成するための設定   |
| `gateway/common.yml` | CP1・CP2 の両方に適用する共通設定 |
| `gateway/cp1.yml`    | CP1 にのみ適用する個別設定      |
| `gateway/cp2.yml`    | CP2 にのみ適用する個別設定      |

`platform_*.yml` で CP を作成し、`gateway/` 配下のファイルで各 CP 内の設定を管理します。 共通部分は `common.yml` にまとめているため、CP ごとのファイルにはその CP 固有の設定だけを記述しています。
