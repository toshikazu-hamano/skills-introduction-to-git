## Step 1: Git によるバージョン管理の概要

あるプロジェクトに取り組んでいて、バックアップの整理が難しくなってきたことに気づきました。しかも、更新の共有方法が人によってばらばらで、共同作業がとても分かりにくい状態です。

少し調べてみて、[Git](https://git-scm.com/) というものを知りました。変更の追跡と他の人との共同作業が簡単になるそうです。ファイル名の付け方の工夫、共有ドライブ、メールでのファイル送付といった古いやり方の分かりにくさを解消してくれます。

> [!IMPORTANT]
> 演習では、Git がすでにインストールされているマシンで Git の使い方を学びます。
> 自分のコンピューターにインストールしたい場合は、環境の組み合わせが多いため、公式の [Git サイト](https://git-scm.com) のインストール手順を参照してください。

### 📖 理論：バージョン管理とは

バージョン管理システムは、コードの変更を長期間管理するときに開発者が直面する、よくある問題を解決します。たとえば次のような問題です。

- バックアップと復旧
- 隔離された環境での実験
- 並行した開発
- ロックされたファイル
- ファイルの重複
- 競合する変更
- チームでの共同作業

次のような場面に出会ったことがあれば、Git のバージョン管理は役に立つはずです。😎

- `my-project-final-v2-really3.zip`
- 「いつから動かなくなった？ 何も変えてないのに！」（本当は変えている）
- 「ファイルがロックされている。彼が月曜に戻るまでコピーで作業しよう。」
- 「v2 が入っていたのはどのメールだっけ？ 先週の水曜のやつかな。」

### 「Git」のバージョン管理とは

Git は[分散バージョン管理システム](https://en.wikipedia.org/wiki/Distributed_version_control)です。つまり、開発者それぞれがプロジェクトの履歴の完全なコピーを持ちます。共有された場所にコピーが 1 つしかない集中型のシステムとは異なります。

分散型には次のような利点があります。

- オフラインで作業できる — ほとんどの操作はローカルで処理されます。
- 堅牢性が高い — 分散したコピーがバックアップとして機能します。
- 柔軟なワークフロー — 開発者は自分のやり方とツールを使えます。

### Git はどうやって使うのか

Git は開発者が開発者のために作った[オープンソース](https://en.wikipedia.org/wiki/Open_source)のツールです。コミュニティは、ほとんどの用途をカバーする機能を作り続けてきました。

たとえば、コミュニティは Git をほぼすべての開発ワークフローに組み込んできました。いくつか挙げます。

- **コマンドラインインターフェイス（CLI）** — 最初からあるツールで、すべての機能の元になっています。
- **コードエディター** — 普段使っているエディター/ツールと一緒に使えます。例：
  - Visual Studio Code
  - JetBrains IDEs
  - Xcode
  - Emacs/VIM
- **ホスティングサービス** — Git を集中管理し、ブラウザーでのオンライン編集もできます。例：
  - GitHub
  - GitLab
  - Gitea
  - Azure DevOps
  - AWS CodeCommit
  - BitBucket
- **デスクトップアプリケーション** — 分かりやすいグラフィカルインターフェイスです。例：
  - GitHub Desktop
  - Sourcetree
  - TortoiseGit
  - GitKraken
  - Git Butler
  - ほかにも多数：https://git-scm.com/tools/guis

### ⌨️ やること：サンプルプロジェクトを開く

Git の練習を始めるため、まずは設定済みの開発環境を開いて、サンプルプロジェクトを見てみましょう。

1. 下のボタンを右クリックして、**Create Codespace** ページを新しいタブで開きます。設定は既定のままにします。

   [![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/{{full_repo_name}}?quickstart=1)

   > 🪧 **注**: 通常、[GitHub Codespace](https://github.com/features/codespaces) にはリポジトリのコードと必要な設定が自動的に含まれます。演習では、ゼロから練習できるように内容を変えてあります。

1. **Repository** 欄が元のリポジトリではなく自分のコピーになっていることを確認し、緑色の **Create Codespace** ボタンをクリックします。

   - ✅ 自分のコピー：`/{{full_repo_name}}`
   - ❌ 元のリポジトリ：`/skills/introduction-to-git`

1. ブラウザーで Visual Studio Code が読み込まれるまで少し待ちます。

1. 左のナビゲーションタブで **File Explorer** を選び、ファイルを表示します。`src/index.html` を右クリックして **Show Preview** を選ぶと、サンプルゲームが動きます。

   > ❗️ **警告**: 何も変更しないでください。
   > まだバージョン管理を追加していません！ 😱

   <img width="350px" src="https://github.com/user-attachments/assets/c5f60f24-27fb-4670-ab0a-c00aa723672c"/><br/>

   <img width="500px" src="https://github.com/user-attachments/assets/a20529f3-8e42-464b-8d84-b0880dd14383"/>

> [!TIP]
> ゲームは開いたままにして、変更を加えながら何度も試してみてください。🧑‍🚀

### ⌨️ やること 2：CLI で Git を使う

まずはコマンドラインインターフェイス（CLI）で Git を使ってみましょう。CLI はすべての Git 機能の元であり、いちばん強力な選択肢です。

1. 統合ターミナルが表示されていない場合は、`Ctrl+Shift+P` を押して `View: Toggle Terminal` を検索・選択して開きます。

   <img width="500px" src="https://github.com/user-attachments/assets/4bbf918a-f87c-4875-b7fd-61d8b16a70e1"/>

1. インストールされている Git のバージョンを表示して、インストールを確認します。

   ```bash
   git --version
   ```

   <img width="500px" src="https://github.com/user-attachments/assets/0e09991b-829f-4028-b951-87bc5fa47bfc"/>

1. Git のヘルプドキュメントを表示します。

   ```bash
   git --help
   ```

   <img width="500px" src="https://github.com/user-attachments/assets/c447adf3-9cc1-4106-9a49-f2bf705d396c"/>

### ⌨️ やること 3：Git の識別情報を設定する

ゲームのバージョン管理を始める前に、変更の作成者として記録されるよう、Git に自分の識別情報を伝えます。

> [!WARNING]
> Git は作成者の名前とメールアドレスを履歴に保存します。名前とメールアドレスは、リポジトリにアクセスできる全員から見えます。GitHub には任意で使える [noreply メールアドレス](https://docs.github.com/en/account-and-profile/reference/email-addresses-reference#your-noreply-email-address)があり、アカウントの[メール設定](https://github.com/settings/emails)から有効にできます。

1. 表示名を設定します。

   ⚠️ `First` と `Last` を自分の情報に置き換えるのを忘れずに。

   ```bash
   git config --global user.name "First Last"
   ```

1. メールアドレスを設定します。プライバシーを守りたい場合は、アカウントの[メール設定](https://github.com/settings/emails)で noreply アドレスを有効にして、個人のメールアドレスを隠すことを検討してください。

   ⚠️ `me@example.com` を自分の情報に置き換えるのを忘れずに。

   ```bash
   git config --global user.email "me@example.com"
   ```

1. 設定を表示して、変更を確認します。

   ```bash
   git config --global --list
   ```

   <img width="500px" src="https://github.com/user-attachments/assets/62688039-3601-4a23-8f61-408210faff0a"/>

1. 作成者の情報を設定したので、Mona が作業を確認しています。少し待って、コメントを見てください。進捗と次の Step が投稿されます。

> [!TIP]
> 複数のアカウントを使っている場合は、プロジェクトごとにユーザー名とメールアドレスを変えることもできます。**既存の**プロジェクトのリポジトリで、`--global` の代わりに `--local` を使います。

<details>
<summary>うまくいかないとき 🤷</summary><br/>

- "First Last" と "me@example.com" を自分の情報に置き換えたか確認してください。

</details>
