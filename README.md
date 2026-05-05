# 図解 HTML（GitHub Pages 用）

**正データ（何をいつ流すか）**は [`uscpa-diagram-delivery`](https://github.com/haitokutaishi-lgtm/uscpa-diagram-delivery) の `schedule/posts.json`。**ここには図解の中身だけ**を置く。

## フォルダ規約

```
diagram-site/
├── topics/
│   ├── _template/          ← 新規テーマはこれをコピーしてリネーム
│   │   └── index.html
│   └── <テーマID>/        ← 英数字・ハイフン推奨（例: lcm-teikahou）
│       └── index.html
└── index.html              ← サイト入口（任意）
```

公開 URL（Pages を `main` ブランチ・ルートにした場合の例）:

`https://<あなたのユーザー>.github.io/diagram-site/topics/<テーマID>/`

## 最短の作業順（毎回）

1. `_template` を `topics/<テーマID>` にコピーする。
2. `topics/<テーマID>/index.html` を編集（図解の本体）。
3. このリポジトリで `git add` → `commit` → `push`（Pages が数分で更新）。
4. 公開 URL をブラウザで確認する。
5. **`uscpa-diagram-delivery` の `schedule/posts.json`** に、配信日（JST）・タイトル・説明・上記 URL を追記して **push**。
6. Discord は **日・水・土 9:00 JST** に自動投稿（その日のキーがある場合のみ）。

## なぜ最初は posts.json を手動更新にしたか

| 手動 | 自動（シート同期など） |
|------|------------------------|
| 実装が単純・壊れにくい | スクリプト・権限・バグの余地が増える |
| **レビュー後だけ反映**しやすい | 「シートを触っただけで即公開」になりやすい |
| | 後からいつでも追加可能 |

**自動化したい場合**は、例として「Google スプレッドシート承認列が TRUE の行だけ JSON を生成して PR を開く」などを後から足せる。**正データは引き続きリポジトリ上の JSON に統合**するのが安全です。

## GitHub Pages の有効化（初回のみ）

リポジトリ **Settings → Pages → Build and deployment → Branch `main` / folder `/ (root)`** を選択して保存。
