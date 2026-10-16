## 開発環境構築

実行には Node.js が必要です


```shell
$ mise trust
$ mise install
$ mise run setup
$ mise run dev
```

開発サーバーは通常 `http://localhost:8080` で起動します。

バックエンドは別途 `http://localhost:3005` で起動してください。接続先は `dev.config.ts` で変更できます。

### mise を使わない場合

```shell
$ npm ci
$ npm run gen-fonts
```

Vetur ではなく Vue (offical) を導入することを推奨しています。

## コミット時の自動フォーマット・lint

このリポジトリでは [husky](https://typicode.github.io/husky/) と [lint-staged](https://github.com/okonet/lint-staged) を利用して、コミット時にステージされたファイルへ自動でフォーマット（prettier）とlint（eslint --fix）が実行されます。

初回セットアップ時は、以下のコマンドを実行してください。

```shell
$ npm run husky:prepare
```

その後は特別な操作は不要で、通常通りコミットするだけで自動的に修正・整形が行われます。

設定ファイル:

- lint-staged: `lint-staged.config.js`
- husky: `.husky/pre-commit`

## コマンド

### ホットリロード環境

```shell
$ npm run dev
```

**実行前に一度`$ npm run gen-fonts`を実行する必要があります**

### ビルド

#### フォント以外のビルド

```shell
$ npm run build
```

#### フォントを含めたビルド

```shell
$ npm run build:with-font
```

#### 絵文字用データの生成

```shell
$ npm run gen-unicode_emojis
```

- リポジトリに生成物が含まれています
- このコマンドは更新用です

#### フォントの生成

```shell
$ npm run gen-fonts
```

リポジトリに生成物が含まれていません

## ビルド成果物の確認

```shell
$ npm run preview
```

**実行前に`$ npm run build`を実行する必要があります**

### テスト/lint

#### ユニットテスト実行

```shell
$ npm run test:unit
```

#### e2e テスト実行

```shell
$ npm run test:e2e
```

`cypress.env.json`を以下の通りに作成する必要があります

```json
{
  "username": "ユーザー名",
  "password": "パスワード"
}
```

`npm run test:e2e-headless`ではヘッドレスで実行できます

#### 再ビルドなしでの e2e テスト実行

```shell
$ npm run test:e2e:without-build
```

#### lint の実行と auto-fix による修正

```shell
$ npm run lint
```

#### lint の実行(auto-fix なし)

```shell
$ npm run lint:no-fix
```

#### 型チェックの実行

```shell
$ npm run type-check
```
