## HTML 生成方法

BUILD.md に従い、Docker 環境を立ち上げ (`docker-compose up`)、[http://localhost:4000/800-63-4/index.ja.html](http://localhost:4000/800-63-4/index.ja.html) にアクセスしてください。

なお、生成された HTML ファイル自体は (特段いじることはないとは思いますが) `/_site/` 以下に配置されます。

## 翻訳ルール

* Definitions で定義された用語は翻訳不要です。
  * 文中にそれらの用語が出てきた場合は英語表記のまま残してください。
* 元の英文を各行毎 (or ブロック) 毎にコメントアウトしつつ、その下に翻訳文を追記してください。
  * 原文と見比べながらのレビューがしやすいです。
* 翻訳担当分を翻訳した後、Pull Request を送ってください。

## 翻訳対象ファイル

`*.ja.md` ファイルのみを編集します。

### メインの翻訳対象ファイル

以下の4つのファイルがメインの翻訳対象です。

* `/sp800-63.ja.md`
* `/sp800-63a.ja.md`
* `/sp800-63b.ja.md`
* `/sp800-63c.ja.md`

なお、以下のファイルはパブコメする人向けなので翻訳不要です。

どうせ英語が読めない人はパブコメもできないでしょうから。

* `/index.ja.html`

### サブの翻訳対象ファイル群

各メインページが Section 毎にサブファイル群を持っているので、それらも翻訳対象になります。

ただし、使われていなかったり翻訳する価値のないファイルは翻訳不要です。

例えば `/sp800-63.ja.md` の翻訳であれば、以下のファイルが対象となり得ます。

* `/sp800-63.ja.md`
* `/_sp800-63/abstract.ja.md`
* `/_sp800-63/acknowledgements.ja.md`
* `/_sp800-63/changehistory.ja.md`
* `/_sp800-63/definitions.ja.md`
* `/_sp800-63/frontmatter.ja.md`
* `/_sp800-63/note-to-reviewers.ja.md`
* `/_sp800-63/sec1_purpose.ja.md`
* `/_sp800-63/sec2_introduction.ja.md`
* `/_sp800-63/sec3_definitions.ja.md`
* `/_sp800-63/sec4_model.ja.md`
* `/_sp800-63/sec5_DIRM.ja.md`
* `/_sp800-63/sec8_references.ja.md`

このうち使われていない (実際にページをレンダリングしてみるとわかります) 以下のファイルは翻訳不要です。

* `/_sp800-63/acknowledgements.ja.md`
* `/_sp800-63/frontmatter.ja.md`

また以下のファイルは英語がわかる人以外が読む価値のないものなので翻訳不要です。

* `/_sp800-63/changehistory.ja.md`
* `/_sp800-63/note-to-reviewers.ja.md`

それ以外のファイルを逐次翻訳してください。

またオリジナルの英語リソースはスペース等含め変更しないでください。

今後 nist 本家のレポジトリから変更を pull してくる際に困ります。
