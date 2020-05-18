# イントロダクション

Denoは、安全なデフォルトを備えたJavaScript/TypeScriptランタイムであり、開発者にとっては素晴らしい経験となるでしょう。

V8, Rust, Tokioで作られています。

## 特徴

- デフォルトでは安全です。明示的に許可しない限り、ファイル、ネットワーク、環境へはアクセスできません。
- TypeScriptをサポートしています。
- 単一の実行ファイル(`deno`)を持ちます。
- 依存性インスペクタ(`deno info`)やコードフォーマッター(`deno fmt`)などの組み込みユーティリティを持っています。
- Denoでの動作が保証された[標準モジュール](https://github.com/denoland/deno/tree/master/std)を持っています。
- スクリプトは単一のJavaScriptファイルにバンドルすることができます。

## Denoの哲学

Denoは、現代のプログラマのための生産的で安全なスクリプトの動作環境を目指しています。

Denoは、常に単一の実行ファイルとして配布されます。

DenoプログラムのURLが与えられれば、[15MB以下のzip形式の実行ファイル](https://github.com/denoland/deno/releases)だけで実行可能です。
Denoはランタイムとパッケージマネージャの両方の役割を明確に担っています。モジュールの読み込みには標準的なブラウザ互換プロトコルを使用します。URLです。

とりわけ、Denoは歴史的にbashやpythonで書かれていたユーティリティスクリプトの代用に最適です。

## ゴール

- 単一の実行ファイル(`deno`)を世に出すこと。
- デフォルトで安全性を提供すること。
  - 特に許可されていない限り、スクリプトはファイル、環境、ネットワークにアクセスできません。
- ブラウザとの互換性: JavaScriptで書かれていて、グローバルな名前空間`Deno`を使用していないDenoプログラムのサブセット(またはそのための機能テスト)は、最新のWebブラウザでも変更なく実行できるようにする必要があります。
- ユニットテスト、コードフォーマット、リントなどの組み込みツールを提供し、開発者の経験を向上させること。
- V8のコンセプトをユーザーランドに漏らさないこと。
- 効率的にHTTPを提供できること。

## Comparison to Node.js

- Deno does not use `npm`
  - It uses modules referenced as URLs or file paths
- Deno does not use `package.json` in its module resolution algorithm.
- All async actions in Deno return a promise. Thus Deno provides different APIs
  than Node.
- Deno requires explicit permissions for file, network, and environment access.
- Deno always dies on uncaught errors.
- Uses "ES Modules" and does not support `require()`. Third party modules are
  imported via URLs:

  ```javascript
  import * as log from "https://deno.land/std/log/mod.ts";
  ```

## Other key behaviors

- Remote code is fetched and cached on first execution, and never updated until
  the code is run with the `--reload` flag. (So, this will still work on an
  airplane.)
- Modules/files loaded from remote URLs are intended to be immutable and
  cacheable.

## Logos

These Deno logos, like the Deno software, are distributed under the MIT license
(public domain and free for use)

- [A hand drawn one by @ry](https://deno.land/images/deno_logo.png)

- [An animated one by @hashrock](https://github.com/denolib/animated-deno-logo/)

- [A high resolution SVG one by @kevinkassimo](https://github.com/denolib/high-res-deno-logo)

- [A pixelated animation one by @tanakaworld](https://deno.land/images/deno_logo_4.gif)
