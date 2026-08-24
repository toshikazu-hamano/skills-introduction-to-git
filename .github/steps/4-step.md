## Step 4: 変更を比較する

「元に戻す」方法が分かったので、次は実際にゲームを変更してみましょう。さらに大事なのは、リポジトリの履歴にコミットする**前**に、何が変わったかを Git に見せてもらう方法を学ぶことです。

ファイルの差分を理解することは、自分の作業を見直し、間違いに気づくために欠かせません。

### 📖 理論：差分（diff）を理解する

Git は記号と色でファイルの変更を示します。

- 緑色の `+` は追加された行
- 赤色の `-` は削除された行

例：

```diff
+ This is a line that was added
- This is a line that was removed
```

> [!TIP]
> 比較に使う既定の色は、次のコマンドで変更できます。
>
> ```bash
> git config --global color.diff.old yellow
> git config --global color.diff.new blue
> ```

### よく使う Git コマンド

`git diff` コマンドは、開発の各状態の間の差分を表示します。

- `git diff` — 作業ディレクトリとステージング領域の差分。
- `git diff --staged` — ステージング領域と 1 つ前のコミットの差分。
- `git diff HEAD~1` — 現在のコミットと 1 つ前のコミットの差分。

### ⌨️ やること 1：差分を見る（CLI）

ゲームに変更を加え、CLI で差分を表示してみましょう。

1. `src/index.html` を開きます。

1. `line 20` で、スコアに関する `info-section` の部分を次の内容に置き換えます。

   ```txt
   <div class="info-section">
      <h3>Current Score</h3>
      <div class="score" id="score">0</div>
      <h3>High Score</h3>
      <div class="high-score" id="high-score">0</div>
   </div>
   ```

   3 種類の変更を確認できます。

   - `Score` のラベルを `Current Score` に変更
   - `High Score` の情報を追加
   - `status` の情報を削除

1. 作業ディレクトリと直前のコミットの差分を表示します。

   ```bash
   git diff src/index.html
   ```

   <img width="500px" src="https://github.com/user-attachments/assets/f41d6917-1651-4549-bb7b-5441a1832e38"/>

1. 変更をステージング領域に上げます。

   ```bash
   git add src/index.html
   ```

1. もう一度同じ比較を実行します。作業ディレクトリがステージング領域と一致したため、差分は表示されません。

   ```bash
   git diff src/index.html
   ```

1. ステージング領域と直前のコミットの差分を表示します。

   ```bash
   git diff --staged src/index.html
   ```

   <img width="500px" src="https://github.com/user-attachments/assets/f6aad38c-56fa-49ed-8209-9fe249c209ff"/>

1. 次のメッセージで変更をコミットします。

   ```md
   git commit -m "Add element for showing high score"
   ```

   <img width="500px" src="https://github.com/user-attachments/assets/8381b943-ca22-4b22-97b5-4520e174fc4c"/>

### ⌨️ やること 2：差分を見る（VS Code）

さらにゲームに変更を加え、今度は VS Code で差分を表示してみましょう。

1. `src/patterns.js` を開きます。

1. `line 3` で、`Null Pointer` の部分を次の内容に置き換え、パターンを変更します。

   ```txt
   {
     name: "Null Pointer",
     pattern: [
       [0, 1, 1, 1, 0],
       [0, 1, 0, 1, 0],
       [0, 1, 1, 1, 0],
       [0, 0, 1, 0, 0],
       [0, 0, 1, 0, 0],
     ],
   },
   ```

1. **File Explorer** で、ファイル名 `patterns.js` の色が変わり、変更済みを示す `M` が付いていることに注目します。

   <img width="350px" src="https://github.com/user-attachments/assets/93a8f34c-9b16-4783-bc46-81532cdeffdf"/>

1. **Source Control** タブを開きます。**Changes** の一覧で `patterns.js` をダブルクリックすると、Diff（比較）ビューが開きます。

   <img width="350px" src="https://github.com/user-attachments/assets/4dce9e42-caca-4c6e-a6fe-8d83d58cd06d"/><br/>

   <img width="500px" src="https://github.com/user-attachments/assets/4c410689-2a53-462f-9200-79d21bddbf2c"/>

   > 💡 **ヒント**: 比較ビューの中で内容を編集すると、すぐに結果を確認できます。

1. ファイルを **staging** 領域に上げます。⚠️ まだコミットしないでください。

   現在のファイルがステージング領域と一致したため、比較ビューに差分が表示されなくなります。

   <img width="500px" src="https://github.com/user-attachments/assets/b1274ece-2b03-42d2-88e8-9f3aaaa8f2c5"/>

1. **Staged Changes** の一覧で `patterns.js` をダブルクリックし、Diff（比較）ビューを開きます。

   ここでは編集できません。コミットに備えて、ステージング領域がロックされているためです。

   <img width="350px" src="https://github.com/user-attachments/assets/da306727-49f1-4f73-9f38-3a0e5d406cef"/><br/>

   <img width="500px" src="https://github.com/user-attachments/assets/de1448eb-d0dd-4ec5-89a2-74fb4aa1cf5f"/>

1. 次のメッセージで変更をコミットします。

   ```txt
   Make null pointer pattern easier to complete
   ```

1. 新しいコミットがリポジトリに追加されたので、Mona が作業を確認しています。少し待って、コメントを見てください。進捗と次の Step が投稿されます。

<details>
<summary>うまくいかないとき 🤷</summary><br/>

- 変更の一覧が 1 画面に収まらない場合は、`q` を押すとスクロール表示を終了できます。

</details>
