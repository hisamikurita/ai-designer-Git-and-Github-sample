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
