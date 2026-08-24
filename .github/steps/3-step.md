## Step 3: Git の履歴を見る

ゲームが Git で追跡されるようになりました。次は、どんな変更が、いつ、誰によって行われたかを調べる方法を学びます。

### 📖 理論：Git の履歴を理解する

Git はコミットによってプロジェクトの完全な履歴を保持します。各コミットには次の情報が含まれます。

- **一意のハッシュ ID**: 履歴の中で簡単に参照するための識別子です。
- **親コミット**: 1 つ前のコミットへの参照です。参照が連なりを作ります。
- **作成者情報**: 誰が変更したか。
- **タイムスタンプ**: いつ変更が適用されたか。
- **コミットメッセージ**: コミットに含まれる変更の説明。

さらに `HEAD` ポインターという特別なラベルがあり、プロジェクト履歴の中で今どこにいるかを示します。自分のプロジェクトは、おそらく次の図のような状態です。

```mermaid
---
config:
  theme: 'forest'
---
gitGraph
   commit id: "9c6ef8a Initial commit"
   commit id: "16ac970 Start game documentation"
   commit id: "762ac02 Start developer docs" tag: "HEAD"
```

### よく使う Git コマンド

履歴の見方は人によって好みが違い、コミュニティが多くの選択肢を作ってきました。
よく使うコマンドとオプションをいくつか挙げます。

- `git log` — プロジェクトの詳しい履歴を表示します。
  - `git log --oneline` — 1 コミットを 1 行で表示します（詳細は減ります）。
  - `git log --graph` — 図として表示します。枝分かれがあるときに便利です。
- `git checkout` — 履歴の別の地点へ移動します（作業ディレクトリのファイルが変わります）。

### ⌨️ やること 1：履歴を見る（CLI）

1. 詳しいコミット履歴を表示します。

   ```bash
   git log
   ```

   <img width="500px" src="https://github.com/user-attachments/assets/87e2aa43-7270-4163-a9e6-5ed5f4f1ed63"/>

1. 1 コミットを 1 行で表示します。

   ```bash
   git log --oneline
   ```

   <img width="500px" src="https://github.com/user-attachments/assets/b49a6352-4233-4903-9254-18eaec569895"/>

1. コミット履歴全体を図で表示します。

   ```bash
   git log --graph --oneline
   ```

   > 🪧 **注**: 履歴が長くなる後の Step で、図の表示はもっと面白くなります。

1. `Initial commit` の **Commit ID** をコピーします。長い形式でも短い形式でも動きます。

1. Commit ID を使って、以前のバージョンを取り出します。

   ```bash
   git checkout <commit id>
   ```

   <img width="500px" src="https://github.com/user-attachments/assets/4d0f6660-e689-47a2-874e-c3d71b32975b"/><br/>

   🪧 `README.md` が消えたことに注目してください。

   <img width="350px" src="https://github.com/user-attachments/assets/65091c64-3bef-47ad-a4ff-82f3260aa903"/>

1. `main` の最新コミットに戻ります。`README.md` が戻ってきます。🧐

   ```bash
   git checkout main
   ```

   <img width="350px" src="https://github.com/user-attachments/assets/5814f14b-fbf5-4090-90f6-32f815f8b773"/><br/>

   <img width="350px" src="https://github.com/user-attachments/assets/fd673876-ca3b-4184-9f7f-c4bf3ae388a6"/>

### ⌨️ やること 2：履歴を見る（VS Code）

1. 左のナビゲーションで **Source Control** タブを開きます。

1. **Changes** の見出しを右クリックし、**Graph** のオプションを有効にします。

   <img width="350px" src="https://github.com/user-attachments/assets/c5bfb32d-198a-4baa-9ae5-156ee283256c"/>

1. **Graph** パネルを見ます。最近のコミットが時系列で並んでいます。

   <img width="350px" src="https://github.com/user-attachments/assets/860f780f-98ca-4c0e-bb0f-e7d65fb84a67"/><br/>

1. コミット名をクリックすると、変更されたファイルの一覧が開きます。

   <img width="350px" src="https://github.com/user-attachments/assets/42310a18-84a4-4dca-8f45-18d589e187c0"/>

1. Git の履歴を見終わったので、Mona が作業を確認しています。少し待って、コメントを見てください。進捗と次の Step が投稿されます。

<details>
<summary>うまくいかないとき 🤷</summary><br/>

- `git log --help` で、履歴表示に使えるオプションをすべて確認できます。

</details>
