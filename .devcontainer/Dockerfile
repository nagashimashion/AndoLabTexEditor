# ベースとなるOSイメージを選択
FROM debian:bookworm-slim

# Dockerビルド中にインタラクティブな問い合わせを無効化する設定
ENV DEBIAN_FRONTEND=noninteractive

# TeX Live（日本語環境を含む）と必要なツールをインストール
# texlive-fullは非常に大きいですが、必要なものがすべて揃うため確実です。
# Gitは論文管理などであると便利なので入れています。
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    texlive-full \
    git \
    && \
    # 不要なキャッシュを削除してイメージサイズを削減
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# この行は、インタラクティブな設定を元に戻すお作法です
ENV DEBIAN_FRONTEND=dialog