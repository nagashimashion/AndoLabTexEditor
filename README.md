# LaTeX開発環境 テンプレート (Docker + VSCode)

DockerとVSCode (Dev Containers) を使用して、クリーンで再現性の高い日本語LaTeX執筆環境を構築するためのテンプレートです。

## ⚠️ 重要な使い方：このリポジトリをどう使うか

このリポジトリは、論文執筆を開始するための「**原本（テンプレート）**」です。

**絶対にこのリポジトリを直接 `git clone` しないでね。俺のメール通知がうるさくなります。**

論文執筆を始めるには、必ず以下の手順で**自分専用の新しいリポジトリを作成**すること。



---

## 🚀 使い方 (執筆開始までの3ステップ)

### ステップ1. テンプレートから自分のリポジトリを作成する

1.  このリポジトリのGitHubページ（`AndoLabTexEditor`）を開きます。
2.  ページ右上にある緑色の「**Use this template**」ボタンをクリックし、「**Create a new repository**」を選択します。
3.  **Repository name**に、あなたの論文用のリポジトリ名（例: `nagashima_thesis`）を入力し、`Private`（非公開）を選択します。
4.  「**Create repository from template**」ボタンを押します。

これで、あなたのGitHubアカウントに、このテンプレートと全く同じ内容の**あなた専用のリポジトリ**が作成されます。

### ステップ2. 自分のリポジトリをローカルPCにクローンする

1.  作成が完了すると、自動的にあなた専用のリポジトリページに移動します。
2.  そのページのURLをコピーし、PCのターミナルで `git clone` を実行します。

    ```bash
    # 注意: URLはあなた専用のリポジトリのものです
    git clone [https://github.com/your-username/my-thesis.git](https://github.com/your-username/my-thesis.git)
    
    # 作成したフォルダに移動
    cd my-thesis
    ```

### ステップ3. VSCodeでコンテナを起動する

1.  クローンしたフォルダをVSCodeで開きます。
    ```bash
    code .
    ```
2.  VSCodeを開くと右下に「**Reopen in Container**」（コンテナーで再度開きます）という通知が表示されるので、それをクリックします。

> **Note**
> 初回はDockerイメージのビルドに数分かかりますが、2回目以降はすぐに起動します。

これで、あなた専用の執筆環境の準備が完了です。

---

## ✍️ 執筆とGitの運用

### ビルドとプレビュー

-   `main.tex`などのLaTeXファイルを編集・保存すると、自動的にビルドが実行されます（`uplatexmk (Build with BibTeX)`レシピ）。
-   ビルドが成功すると、`out`ディレクトリにPDFが生成されます。
-   VSCodeの右上にある`LaTeX Workshop`のPDFプレビューボタンで確認できます。

### 変更の保存 (Git)

執筆した内容は、**あなた専用のリポジトリ**に自由にコミット(記録)・プッシュ(送信)してください。

```bash
# 変更内容をステージング
git add .

# 変更内容をコミット（:memo: はGitmojiの絵文字です）
git commit -m ":memo: 第1章の草稿を執筆"

# あなた専用のGitHubリポジトリにバックアップ
git push
```

この運用により、原本のテンプレートを汚すことなく、あなたの作業だけを安全にGitHubで管理できます。

### 手動でのクリーンアップ
もし中間ファイルが残ってしまった場合は、以下の手順で手動クリーンを実行できます。

VSCodeの左側にあるTeXのアイコン (LaTeX Workshop) をクリックします。

COMMANDS > LaTeXプロジェクトをビルド をクリックします。

表示されたレシピ一覧から「Clean All Auxiliary Files (Manual)」を選択して実行します。

## ✨ 特徴
- 環境の分離: Dockerを使用するため、ローカルPCにTeX Liveなどをインストールする必要がありません。

- 再現性の担保: チームメンバーや他のPCでも、全く同じ環境を数コマンドで再現できます。

- シームレスな開発体験: VSCode Dev Containersにより、コンテナ内での開発を意識させないシームレスな操作が可能です。

- 日本語環境対応: upLaTeXとBibTeX（日本語対応）を導入済みです。

- 自動クリーン機能: ビルドが成功するたびに、補助ファイル（.aux, .logなど）が自動で削除されます。

- デバッグ支援: Error LensやSpell Checkerなどの拡張機能が標準で導入されます。

## 🔧 必要なもの
以下のツールがPCにインストールされている必要があります。

- [Docker Desktop](https://www.docker.com/products/docker-desktop/)

- [Visual Studio Code](https://code.visualstudio.com/)

- [Dev Containers (VSCode拡張機能)](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

### 【Windowsユーザー向け】Docker Desktop インストールガイド
DockerをWindowsで動作させるには、WSL2 (Windows Subsystem for Linux 2) という基盤システムが必要です。
1. コントロールパネルを開き、「プログラム ＞ Windowsの機能の有効かまたは無効化」をクリックします。

1. 「Linux Windows サブシステム」と「Virtual Machine Platform」にチェックを入れてOKをクリックします。

1. Microsoftストアから「Ubuntu」（例: Ubuntu 22.04 LTS）を入手し、インストールします。

1. インストールが終わったら、Ubuntuを起動し、指示に従ってユーザー名とパスワードをセットアップします。

1. 上記の手順は、WSL2錠でDpckerを運用したい場合に行う

1. [Docker Desktopの公式サイト](https://www.docker.com/ja-jp/products/docker-desktop/)から、インストーラーをダウンロードします。

1. インストーラーを起動し、指示に従ってインストールします。（この時も「Use WSL 2」が推奨されます）

1. インストール完了後、Docker Desktopを起動し、設定（歯車アイコン） > 「Resources > WSL integration」に移動します。

1. 「Enable integration with my default WSL distro」にチェックを入れ、一覧からインストールした「Ubuntu」のトグルをオンにして、「Apply & Restart」をクリックします。

## 📁 ファイル構成
```
.
├── .vscode/
│   └── settings.json  # VSCodeエディタとLaTeX Workshopの設定ファイル
├── .devcontainer/
│   ├── devcontainer.json  # 開発コンテナの定義 (導入する拡張機能など)
│   └── Dockerfile         # LaTeX環境(Dockerイメージ)の設計図
├── .gitignore             # Gitの追跡対象外ファイルを指定
├── main.tex               # (サンプル) LaTeXのソースファイル
└── README.md              # このファイル
```
## 🎨 カスタマイズ
環境のカスタマイズは、以下のファイルを編集してコンテナをリビルドすることで行います。

インストールするLinuxパッケージの変更: .devcontainer/Dockerfile

VSCode拡張機能の追加/削除: .devcontainer/devcontainer.json

LaTeXやエディタの動作設定変更: .vscode/settings.json
