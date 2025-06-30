# LaTeX開発環境 テンプレート (Docker + VSCode)

DockerとVSCode (Dev Containers) を使用して、クリーンで再現性の高い日本語LaTeX執筆環境を構築するためのテンプレートです。

## ✨ 特徴

- **環境の分離**: Dockerを使用するため、ローカルPCにTeX Liveなどをインストールする必要がありません。
- **再現性の担保**: チームメンバーや他のPCでも、全く同じ環境を数コマンドで再現できます。
- **シームレスな開発体験**: VSCode Dev Containersにより、コンテナ内での開発を意識させないシームレスな操作が可能です。
- **日本語環境対応**: upLaTeX/upBibTeX (ptex-ng) を含む`texlive-full`を導入済みです。
- **自動クリーン機能**: ビルドが成功するたびに、補助ファイル（`.aux`, `.log`など）が自動で削除されます。
- **手動クリーン機能**: 必要に応じて、すべての補助ファイルを手動で一掃するコマンドも用意しています。

## 🔧 必要なもの

以下のツールがPCにインストールされている必要があります。

- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Visual Studio Code](https://code.visualstudio.com/)
- [Dev Containers (VSCode拡張機能)](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

## 🚀 使い方

1.  **リポジトリをクローン**
    ```bash
    git clone <このリポジトリのURL>
    cd <クローンしたディレクトリ名>
    ```

2.  **VSCodeで開く**
    ```bash
    code .
    ```

3.  **コンテナで再度開く**
    VSCodeを開くと右下に「Reopen in Container」という通知が表示されるので、クリックしてください。
    
    > **Note**
    > 初回はDockerイメージのビルドに数分かかることがあります。

4.  **執筆とビルド**
    - `main.tex`などのLaTeXファイルを編集・保存すると、自動的にビルドが実行されます（`uplatexmk (Build)`レシピ）。
    - ビルドが成功すると、`out`ディレクトリにPDFが生成され、同時に補助ファイルは自動でクリーンアップされます。

5.  **手動でのクリーンアップ**
    もし補助ファイルが残ってしまった場合や、意図的にクリーンしたい場合は、以下の手順で手動クリーンを実行できます。
    1. VSCodeの左側にあるTeXのアイコン (LaTeX Workshop) をクリックします。
    2. `COMMANDS` > `LaTeXプロジェクトをビルド` をクリックします。
    3. 表示されたレシピ一覧から「**Clean All Auxiliary Files (Manual)**」を選択して実行します。

## 📁 ファイル構成

```
.
├── .devcontainer/
│   ├── devcontainer.json  # VSCodeと拡張機能の設定ファイル
│   └── Dockerfile         # LaTeX環境(Dockerイメージ)を定義するファイル
├── .gitignore             # Gitの追跡対象外ファイルを指定
├── main.tex               # (サンプル) LaTeXのソースファイル
└── README.md              # このファイル
```

## 🎨 カスタマイズ

環境のカスタマイズは、`.devcontainer/`内のファイルを編集することで行います。
- **VSCodeの拡張機能や設定の変更**: `.devcontainer/devcontainer.json`
- **インストールするLinuxパッケージの変更**: `.devcontainer/Dockerfile`