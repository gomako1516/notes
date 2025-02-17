# notes
学習・情報などドキュメント用リポジトリ。

# リポジトリ命名規則
| 用途                          | 命名ルール               | 例                                |
|-------------------------------|--------------------------|-----------------------------------|
| 学習用                        | study-技術名            | study-react-xxx-app, study-nextjs, study-css |
| アウトプット（制作物）         | project-アプリ名         | project-todo-app, project-map-viewer |
| 学習メモ・技術ノート           | notes-カテゴリ           | notes-js, notes-ui-design         |
| アルゴリズム・競技プログラミング | study-algorithms         | study-algorithms, study-leetcode  |
| 試作・検証用コード             | sandbox-技術名           | sandbox-deckgl, sandbox-webgl     |
| ブログや記事                   | blog-カテゴリ            | blog-react-hooks, blog-maplibre   |

# Markdown記法 チートシート
## 見出し
\```md
# H1 見出し
## H2 見出し
### H3 見出し
#### H4 見出し
##### H5 見出し
###### H6 見出し
\```

## 強調
\```md
**太字**
__太字__

*斜体*
_斜体_

~~打ち消し線~~
\```

## 箇条書き
\```md
- リスト1
  - リスト1-1
  - リスト1-2
- リスト2
\```

\```md
1. 項目1
2. 項目2
   1. 項目2-1
   2. 項目2-2
3. 項目3
\```

## コードブロック
\```js
console.log("Hello, World!");
\```

## 引用
\```md
> これは引用です
>> ネストされた引用
\```

## リンク
\```md
[GitHub](https://github.com/)
\```

## 画像
\```md
![GitHub Logo](https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png)
\```

## テーブル
\```md
| 名前  | 年齢 | 職業     |
|------|----|---------|
| 太郎  | 25 | エンジニア |
| 花子  | 30 | デザイナー |
\```

## チェックリスト
\```md
- [x] タスク1
- [ ] タスク2
- [ ] タスク3
\```