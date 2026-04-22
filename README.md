# 🌱 AI時代のデザイナーのためのGit・GitHub入門 🌱

Claude Code や Codex や Figma Make を使って、実際に動くプロトタイプを爆速で作り上げていく時代、**AIツールの登場でデザイナーがコードを書く場面は確実に増えています。**

「コミットする」「プルする」「ブランチを切る」といった**操作自体は、AIに指示すれば簡単にできてしまいます**。このドキュメントでは `git add` のようなコマンドはあえて扱いません。それよりも、**Gitの概念を理解すること**に集中してもらえたらと思っています。概念さえわかれば、チーム開発への入りやすさがぐっと変わるはずです。

はじめます！

<img width="1280" height="640" alt="figmadetukutta" src="https://github.com/user-attachments/assets/0de27c35-cfa5-4634-a694-c426b6049908" />

# 概念編

## GitとGitHubは別物

まず最初に、混同されやすいこの2つを整理しましょう。

| | Git | GitHub |
|---|---|---|
| **何？** | 変更履歴を管理する仕組み（ソフトウェア） | Gitの履歴をオンラインで共有できるサービス |
| **誰が作った？** | Linus Torvalds（個人） | Microsoft傘下の企業 |
| **場所** | 自分のPC上で動く | インターネット上（クラウド） |
| **例え** | 日記帳そのもの | 日記帳を預けて共有できる図書館 |

**Gitが土台の技術**で、**GitHubはそれを活かしたWebサービス**です。
GitはGitHubなしでも使えますが、チームで共同作業するためにGitHubを組み合わせるのが一般的です。

<img width="1280" height="640" alt="figmadetukutta02" src="https://github.com/user-attachments/assets/dd65ef5f-367a-473d-8421-5743143801b7" />

## Gitって何？

Gitとはファイルの変更履歴を管理するツールです。デザイナーにとって身近な例で言うと…

```
logo_v1.png
↓
logo_v2.png
↓
logo_v2_final.png
↓
logo_v2_final_本当に最終.png
```
こうなりがちなファイル管理をGitを使うとスッキリ解決できます。
ファイル名を変えなくても「**いつ・誰が・何を変えたか**」を記録してくれます。

<img width="1280" height="640" alt="figmadetukutta03" src="https://github.com/user-attachments/assets/1c54acdf-70f9-4067-bac9-ab4f85194d0b" />
<br/>

また、複数人で同じプロジェクトを触るときにも力を発揮します。

Figmaでは複数人が同じファイルをリアルタイムで編集できますが、コードファイルはそうはいきません。Gitを使うことで、それぞれがローカルで作業した変更を後からひとつにまとめることができます。

たとえば、あなたがヘッダーを、Aさんがカードコンポーネントを、Bさんがフッターをそれぞれ別々に作業していても、Gitが自動でひとつに統合してくれます。Figmaの共同編集を、コードファイルで実現するイメージです。

<img width="1280" height="640" alt="figmadetukutta13" src="https://github.com/user-attachments/assets/cbac3509-a281-43b6-a05c-8ed92525bc96" />

## 覚えておきたい7つの言葉

### 1. リポジトリ（Repository）

<img width="1280" height="640" alt="Group 81" src="https://github.com/user-attachments/assets/cb934a9e-4124-4129-9d8c-85e5bb6315bd" />
<br/>

プロジェクトのファイルと変更履歴をまとめて保管する**箱**のようなものです。

- **ローカルリポジトリ** : 自分のPC上にある箱
- **リモートリポジトリ** : GitHub上にある共有の箱

作業は常にローカルで行い、完成したらリモートに送る、というサイクルで進みます。

### 2. クローン（Clone）

<img width="1280" height="640" alt="figamdetukutta10" src="https://github.com/user-attachments/assets/a603938d-bac1-4885-81f5-b97423ec1ddf" />
<br/>

リモートリポジトリ（GitHub上の箱）を、自分のPC上に丸ごとコピーしてくる操作です。
**チームのプロジェクトに初めて参加するとき、最初の一回だけ行います。**
> クローンしたあとは、後述するプル(Pull)で最新の変更を取り込みながら作業を続けます。

### 3. コミット（Commit）

<img width="1280" height="640" alt="figmadetukutta06" src="https://github.com/user-attachments/assets/46b7e3c1-963b-4349-a24a-0f273c0a3dbf" />
<br/>

変更内容を**記録**すること。「どんな変更をしたか」のメモ（コミットメッセージ）を一緒に残します。

ゲームのセーブポイントと同じで、いつでもその時点に戻れます。こまめにコミットしておくと安心です。

### 4. ブランチ（Branch）/ マージ(Merge)

<img width="1280" height="640" alt="figmadetukutta07" src="https://github.com/user-attachments/assets/0d32affb-14ab-4e78-866d-3036368d75c4" />
<br/>

ブランチは作業用の複製を作成します。本番のファイルをそのままに、複製した方で安全に作業できます。

作業が完了してレビューを経たら、本番にマージ(合流)します。

### 5. ステージング（Staging）

<img width="1280" height="640" alt="figmadetukutta08" src="https://github.com/user-attachments/assets/357e5e5a-c2e5-40a0-9544-b7a17a53ee9c" />
<br/>

コミットの前に「**何をセーブ対象に含めるか**」を選ぶ準備作業です。  
複数のファイルを変更していても、関係するものだけを選んでコミットできるので、履歴が整理されます。

### 6. プッシュ／プル（Push / Pull）

<img width="1280" height="640" alt="figmadeyukutta09" src="https://github.com/user-attachments/assets/fbd239df-659f-4f19-9a86-794d267c4765" />
<br/>

- **Push**：自分のPC（ローカル）→ GitHubへアップロード
- **Pull**：GitHub → 自分のPCへダウンロード（チームの最新変更を取り込む）

作業前は必ずPullして、自分の手元を最新の状態にしておく習慣をつけましょう。

### 7. プルリクエスト（Pull Request / PR）

<img width="1280" height="640" alt="figmadetukutta11" src="https://github.com/user-attachments/assets/f5a288c4-5505-4948-9fed-1c350a3e4c83" />
<br/>

「このブランチの変更を、本番に取り込んでいいですか？」とチームに確認を求める仕組みです。

作業ブランチをPushしたあと、GitHub上でプルリクエストを作成します。
エンジニアやチームメンバーがコードをレビューし、問題なければマージ(Merge)されます。

<img width="1280" height="641" alt="figamdetukutta12" src="https://github.com/user-attachments/assets/f51ca369-9886-4724-aa5a-1010d542a2c4" />

## 基本的な作業の流れ

```
① Clone or Pullする（チームの最新状態を取り込む）
        ↓
② ブランチを作る（自分の作業用スペースを用意）
        ↓
③ ファイルを編集する
        ↓
④ ステージング
        ↓
⑤ コミット（変更内容をセーブ）
        ↓
⑥ Pushする（GitHubに送る）
        ↓
⑦ プルリクエストを出す（エンジニアにレビュー依頼）
        ↓
⑧ OKが出たらMergeする

```

ざっくりこの流れを1サイクルとして、作業ごとに繰り返します。

<img width="1280" height="640" alt="figamdetukutta14" src="https://github.com/user-attachments/assets/828408f8-249e-40ef-9d08-551d498bf167" />

# 実践編

Gitの全容がざっくりイメージできたら、実際にClaude Codeを使ってGitを操作してみましょう。よりGitのイメージが具体化されるはずです。

もう一度お伝えすると、このドキュメントでは `git add`のようなコマンドはあえて扱いません。Git操作はすべてClaude Codeに指示してもらいます。

## はじめる前に

実践編を進めるにあたって、以下が済んでいることを確認してください。

- `Claude Codeがインストールされていること` インストール方法は[公式ドキュメント](https://docs.anthropic.com/ja/docs/claude-code)を参照してください。

- `Visual Studio Code（VSCode）がインストールされていること` まだの場合は[公式サイト](https://code.visualstudio.com/)からインストールしてください。

- `GitHubアカウントを持っていること` まだの場合は[GitHub](https://github.com/)からアカウントを作成してください。

## 1. GitHub CLIをインストールする

プルリクエストの作成やSSHキーの登録をClaude Codeから行うために、GitHub CLI（`gh`）が必要です。Claude Codeに指示してインストールします。

```claude code
GitHub CLI（gh）をインストールして、GitHubアカウントと連携してください。
```

途中でブラウザが開いて認証を求められます。画面の指示に従って認証を完了させてください。

## 2. SSHキーを生成・登録する

GitHubと安全に通信するための「鍵」を作ります。Claude Codeにそのまま貼り付けて指示してください。

```claude code
SSHキーを生成して、GitHub CLIを使ってGitHubに登録してください。
メールアドレスは「GitHubに登録しているメールアドレス」です。
すでに鍵がある場合はそのまま教えてください。
```

完了したら、Claude Codeに接続確認を指示します。

```claude code
GitHubとのSSH接続が成功しているか確認してください。
```

`Hi ユーザー名! You've successfully authenticated`か接続されているという内容が返ってくれば成功です。

## 3. GitLensとGit Graphのインストール

VSCodeを開いて、左側の拡張機能アイコン（四角が4つのアイコン）をクリックし、`GitLens`と`Git Graph`検索してインストールします。GitLensはVSCode内での「Gitを用いた開発」を便利にする拡張機能で、Git GraphはGitリポジトリの履歴やブランチを視覚化し、操作を容易にするための拡張機能です。


<img alt="スクリーンショット 2026-04-01 21 08 56" src="https://github.com/user-attachments/assets/8e332032-f0e8-4234-a64c-faba4a38ece1" width="49%" />
<img alt="スクリーンショット 2026-04-02 12 54 11" src="https://github.com/user-attachments/assets/5901e74f-3959-4ad3-a939-ebcb48b9c54a" width="49%" />
<br/>
<br/>

初心者のうちはGit Graphでなくても `Sourcetree` や `GitKraken` などのGUIツールを併用するようにしましょう。Claude Codeが何をしたかを視覚的に把握することで、Gitの概念が自然と身についていきます。

## 4. GitHubでリモートリポジトリを作成してCloneする

まずブラウザでGitHubを開き、リモートリポジトリを作成します。

1. GitHubの右上の 「+」 アイコンから 「New」 を選択
2. Repository name にプロジェクト名を入力
3. 「Add README」をONにしてください
4. 「Create repository」 をクリック

<img alt="スクリーンショット 2026-04-01 21 21 55" src="https://github.com/user-attachments/assets/1614d4f2-df59-49f1-b274-042341859b2b" width="49%" />
<img alt="スクリーンショット 2026-04-02 12 58 12" src="https://github.com/user-attachments/assets/e1704101-5c11-42f6-8286-2045c60831b0" width="49%" />
<br/>
<br/>

README.mdが入ったリモートリポジトリが作成されました 🙌

<img width="1512" height="905" alt="スクリーンショット 2026-04-02 14 29 10" src="https://github.com/user-attachments/assets/44c0c7a6-449f-4df2-a52a-4adf1e540317" />
<br/>
<br/>

作成後に表示されるリモートリポジトリのURLをコピーして、ターミナルからClaude Codeに指示します。

```claude code
以下のリポジトリをSSHでCloneしてください。
https://github.com/〇〇/〇〇.git
```

おそらくホームディレクトリ下にフォルダが作成されていると思うので、VSCodeでそのフォルダを開いてください。これでクローンが完了して、ローカルリポジトリが作成されました🙌

ここで、Clone 直後のGitの状態を確認してみましょう。

ブランチタブに切り替えて、View Git Graph アイコンを押下すると mainブランチに「Initial commit」というメッセージでコミットされていることがわかりますね。

ここからブランチを切ってプルリクエストの作成からマージまでを体験していただきます🙏

<img alt="スクリーンショット 2026-04-02 14 50 39" src="https://github.com/user-attachments/assets/fd66f6ca-90af-45d6-8fee-69b5e96d5b82" width="49%" />

<img alt="スクリーンショット 2026-04-02 14 49 44" src="https://github.com/user-attachments/assets/64fcdc24-cf67-46a9-bd3d-bd52fb0bb98c" width="49%" />

## 5. ブランチを作成

作業を始める前に、必ずブランチを作ります。

```claude code
「feature/プロトタイプ修正」というブランチを作って切り替えてください。
```

VSCodeの左下の表示がブランチ名に変わっている、またはGit Graph で `origin/main` の横に `feature/プロトタイプ修正` のラベルが表示されていれば、`feature/プロトタイプ修正`ブランチに切り替わっています。

<img width="1512" height="982" alt="スクリーンショット 2026-04-02 14 46 09" src="https://github.com/user-attachments/assets/16276349-5a13-4176-8d38-9deb23e14a5c" />

## 6. ファイルを編集・コミットする

ファイルを編集したら、Claude Codeにコミットを指示します。

```claude code
README.mdに適当な記述をしてコミットしてください。メッセージは「テストコミット」でお願いします。 
```

<img width="49%" alt="スクリーンショット 2026-04-02 18 58 48" src="https://github.com/user-attachments/assets/ca58df15-c911-4d92-8136-a0c50e6646a1" />
<img width="49%" alt="スクリーンショット 2026-04-02 18 46 56" src="https://github.com/user-attachments/assets/845807bd-c313-4966-93b2-4c1047f2d75d" />
<br/>
<br/>

これでコミットされたのですが、少し全体が分かりにくいので、一度mainブランチに切り替えてみてください。

Git Graph のmainラベルをダブルクリックするか、Claude Codeにmainブランチに切り替えてみてください。と指示してみてください。mainブランチから`feature/プロトタイプ修正`ブランチが派生して「テストコミット」のメッセージでコミットされているのがわかります🙌


<img width="1512" height="982" alt="スクリーンショット 2026-04-02 19 23 12" src="https://github.com/user-attachments/assets/44525a56-cc45-47ee-915d-5931bf37ad86" />

## 7. Pushする

コミットが終わったら、GitHubに送ります。

```claude code
`feature/プロトタイプ修正`ブランチへ移動して変更をPushしてください。
```

同様に現在のブランチではプッシュされたか視覚的にわからないので、一度mainブランチへ切り替えて Git Graph を見てみてください。 `feature/プロトタイプ修正`ブランチの横に`origin`とついたのが分かります。これがGitHub上（リモート）の現在地を示します。ローカルとリモートが同じ地点にいる、すなわち**手元の変更がGitHubに反映された状態**ということです。


<img width="1512" height="982" alt="スクリーンショット 2026-04-02 19 29 31" src="https://github.com/user-attachments/assets/dad24603-577c-40c7-a641-3c990c075249" />

## 8. プルリクエストを作成する

最後にプルリクエストを作成します。

```claude code
feature/プロトタイプ修正のプルリクエストを作成してください。
タイトルは「テストコミット」、
本文には変更内容の概要を書いてください。
```

GithubのPull requestタブを見てみるとClaude Codeがそのままプルリクエストを作成してくれているのがわかります🙌

<img width="3024" height="2771" alt="FireShot Capture 016 - Pull requests · hisamikurita_ai-designer-git-sample -  github com" src="https://github.com/user-attachments/assets/96ae8c11-eea8-4db5-a488-f18c800c5fea" />

## 9. マージしてみる

本来の開発ではここでエンジニアのレビューが入りますが、練習なので緑の「Merge pull request」ボタンを押下してマージしてみてください。

<img width="1512" height="905" alt="スクリーンショット 2026-04-02 19 45 38" src="https://github.com/user-attachments/assets/9ebb59c8-725d-4bf0-9ee4-05e7438828d3" />

リモートリポジトリのREADME.mdをみると変更が反映されていることがわかります🙌

ここでVSCodeに戻ってmainブランチに切り替えて、README.mdを確認してみてください。変更が反映される前の状態なっていますね...

また、Git Graphも確認してみましょう。ちょっと歪なグラフになっています💦

<img width="1512" height="982" alt="スクリーンショット 2026-04-02 19 47 51" src="https://github.com/user-attachments/assets/b962b26d-2d88-4136-b21d-ba73696d46e3" />
<br/>

ここで注意して欲しいのが、**マージはリモート上で行われたので、ローカルのmainブランチはまだ古い状態です**。「歪なグラフ」とはローカルとリモートがズレている状態ですね。

Claude CodeにmainをPullしてもらうと、グラフが一直線に整い、ローカルのmainブランチのREADME.mdも最新に反映されます。

```claude code
mainブランチに切り替えてPullしてください。
```

<img width="1512" height="982" alt="スクリーンショット 2026-04-02 19 52 53" src="https://github.com/user-attachments/assets/d5035b60-4ea4-4b58-ad80-56458e4f6e39" />
<br/>

変更が反映されない場合は Git Graph の リフレッシュアイコンを押下してみてください。

これで、ローカルとリモートが一致したので、別の作業のためにmainブランチから作業用のブランチを切って作業する準備も整いました。

一連のサイクルはこれで完了です🙌

**このようにGit操作をするときは、今いるブランチとローカルとリモートの状態を常にGit Graphで視覚的に確認する習慣をつけましょう。**

# 応用編

実践編でGitの基本的な流れを掴んだら、より実務で発生するトラブルや共通認識を覚えましょう。

## 1. Git Flow — ブランチ戦略

実際のチーム開発では、ブランチの使い方にルールを設けるのが一般的です。その代表的な戦略が **Git Flow** です。

| ブランチ | 役割 |
| -------- | -------- |
| main     | 本番環境。常に動く状態を保つ    |
| develop     | 開発の統合ブランチ。次のリリースに向けた作業をまとめる    |
| feature/〇〇     | 機能ごとの作業ブランチ。developから切る    |
| release/〇〇     | リリース前の最終調整ブランチ    |
| hotfix/〇〇     | 本番のバグを緊急修正するブランチ    |

### 基本的な流れ

```
develop から feature/〇〇 を切る
        ↓
feature/〇〇 で作業・コミット
        ↓
develop へプルリクエスト → マージ
        ↓
リリースのタイミングで develop → main へマージ
```

ブランチ戦略の概要と**main / develop ブランチで直接作業してプッシュしない。作業前に必ず feature/〇〇 ブランチを切る** ということだけ覚えておきましょう。

<img width="1280" height="640" alt="figmadetukutta14" src="https://github.com/user-attachments/assets/556e6ee3-96a4-4480-ade6-86975da1eae2" />

## 2. コミットメッセージの書き方ルール

コミットメッセージはチーム全員が読む履歴になります。後から見返したときに何をしたかが一目でわかるように書くか、**AIにコミットメッセージも含めて書いてもらいましょう。**

### よく使われるプレフィックス

| プレフィックス | 意味 | 例 |
|---|---|---|
| `feat:` | 新しい機能の追加 | `feat: ヘッダーコンポーネントを追加` |
| `fix:` | バグ修正 | `fix: ボタンのクリックが効かない問題を修正` |
| `style:` | デザイン・スタイルの変更 | `style: フォントサイズを調整` |
| `docs:` | ドキュメントの更新 | `docs: READMEを更新` |
| `chore:` | 設定や雑務 | `chore: 不要なファイルを削除` |

### Claude Codeへの指示例

```claude code
変更をコミットしてください。
メッセージは「feat: トップページのビジュアルを修正」でお願いします。
```

## 3. Pullするタイミングと事故の防ぎ方

コンフリクト（次の章で説明します）の多くは、Pullを忘れたまま作業を進めることで起きます。以下のタイミングでPullする癖をつけましょう。

### Pullすべきタイミング

- **作業を始める前** — 必ず最新の状態に更新してから作業を始める
- **長時間作業した後** — チームの変更が溜まっている可能性がある
- **ブランチを切る前** — 古い状態からブランチを切るとコンフリクトが起きやすい

### Claude Codeへの指示例

```claude code
developブランチの最新の変更をPullしてください。
```

Pullした後にGit Graphを見て、`origin/develop`と`develop`が同じ地点に揃っていれば最新の状態です。ズレていたら再度Pullしましょう。

## 4. コンフリクトの解決

コンフリクトとは同じファイルの同じ箇所を、複数人が別々に編集してマージしようとしたときに発生します。Gitがどちらの変更を採用すればいいか判断できない状態です。

**言い換えるとGitがどちらを残すべきか親切に聞いてくれている状態とも言えます。**

<img width="1280" height="640" alt="figamdetukuttta20" src="https://github.com/user-attachments/assets/e4313b4f-d021-457f-af8e-2372bc45c5dc" />
<br/>

コンフリクトが起きても慌てなくて大丈夫です。Claude Codeに解決を任せましょう。

```claude code
コンフリクトが発生しています。内容を確認して解決してください。
どちらの変更を採用するか判断が難しい場合は教えてください。
```

Claude Codeが判断できない場合、どちらの変更を残すかはエンジニアと相談して決めましょう。VSCodeではコンフリクトが発生したファイルに以下のような表示が出ます。

```
<<<<<<< HEAD
自分の変更内容
=======
相手の変更内容
>>>>>>> feature/〇〇
```

「自分の変更を残す」「相手の変更を残す」「両方残す」の3択から選んでClaude Codeに指示します。

```claude code
コンフリクトは自分の変更内容を優先して解決してください。
```

## 5. 誤ったブランチにコミットしたときの対処

よくあるミスとして、mainやdevelopに直接コミットしてしまった、feature/Aで作業するつもりがfeature/Bにコミットしてしまった、というケースです。

焦らずClaude Codeに状況を伝えましょう。

```claude code
誤ってmainブランチにコミットしてしまいました。
直前のコミットを取り消して、変更内容は残したままにしてください。
```

Pushする前であれば自分のローカルリポジトリだけの影響で済むので大丈夫です。 **Pushしてしまったら本番かテスト環境に反映されてしまう可能性もあるため、至急エンジニアに相談しましょう。**

## 6. レビューで指摘を受けたときの対処

プルリクエストを出した後、エンジニアから修正依頼が来ることがあります。慌てず以下の流れで対応しましょう。

### 基本的な流れ

```
① GitHubのプルリクエストページでコメントを確認する
        ↓
② 同じfeatureブランチで修正作業を行う
        ↓
③ コミット・Pushする
        ↓
④ 同じプルリクエストに自動で反映される
        ↓
⑤ エンジニアに再レビューを依頼する
```

<img width="1280" height="640" alt="Group 157" src="https://github.com/user-attachments/assets/5b955ada-09cf-4f08-a13e-cb025327e38d" />
<br/>

新しくプルリクエストを作り直す必要はありません。同じブランチにPushするだけで、既存のプルリクエストに変更が追加されます。

### Claude Codeへの指示例

```claude code
feature/〇〇に切り替えて、
〇〇を修正してコミット・Pushしてください。
メッセージは「fix: レビュー指摘を修正」でお願いします。
```

この応用編の内容が身につけば、エンジニアとのチーム開発がよりスムーズになるはずです！

# 終わりに

AIツールの登場でデザイナーがコードを書く場面が増えた今、Gitはデザイナーとエンジニアをつなぐ共通言語になりつつあるはずです。完璧に使いこなす必要はありません。

概念を理解して、Claude Codeを頼りながら少しずつ慣れていきましょう⭐️

たぶん、エンジニアはデザイナーさんにGitを使って欲しいと多くの人が思っているはずです。
