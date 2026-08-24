# Introduction to Git（日本語版）

_コマンドライン（CLI）と VS Code を使い、Git のバージョン管理でゲームを開発する。_

> このリポジトリは GitHub Skills「[Introduction to Git](https://github.com/skills/introduction-to-git)」（MIT License）の日本語版です。
> 演習の進め方と自動チェックの仕組みは原本と同じで、Issue に投稿される手順の本文だけを日本語にしています。

## ようこそ

- **対象**: Git のバージョン管理を学びたい、開発を始めたばかりの人
- **学ぶこと**: コミット、ブランチ、履歴、共同作業の基礎といった Git の基本
- **作るもの**: Git リポジトリを作り、サンプルコードを追加して、簡単な機能を開発します
- **前提**:

  - Git やバージョン管理の経験は不要です。
  - 推奨: コマンドラインインターフェイス（CLI）の基本的な操作に慣れていること。
  - 推奨: Visual Studio Code の基本的な操作に慣れていること。

- **所要時間**: 60 分以内

この演習で行うこと:

1. バージョン管理とは何か、開発者がなぜ使うのかを理解する
2. Git の識別情報を設定する
3. 最初のリポジトリを作り、コミットする
4. プロジェクトの履歴を見て、ファイルの差分を比較する
5. ブランチを使って安全に試す
6. Git の共同作業の考え方を学ぶ

### 演習の始め方

演習を自分のアカウントにコピーし、Octocat（Mona）が最初のレッスンを準備するまで **20 秒ほど**待ってから、**ページを再読み込み**してください。

[![](https://img.shields.io/badge/Copy%20Exercise-%E2%86%92-1f883d?style=for-the-badge&logo=github&labelColor=197935)](https://github.com/new?template_owner=mamezou&template_name=skills-ja-introduction-to-git&owner=%40me&name=skills-introduction-to-git&description=Exercise:+Introduction+to+Git&visibility=public)

<details>
<summary>うまくいかないとき 🤷</summary><br/>

演習をコピーするときは、次の設定を推奨します。

- Owner は自分の個人アカウント（または演習を置く Organization）を選ぶ。

- private リポジトリは Actions の実行時間を消費するため、public リポジトリを推奨します。

20 秒待っても演習が始まらないときは、[Actions](../../actions) タブを確認してください。

- ジョブが実行中かどうかを見る。少し長くかかることがあります。

- ジョブが失敗している場合は、講師に知らせてください。

</details>

---

&copy; 2025 GitHub &bull; [Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](https://gh.io/mit)
