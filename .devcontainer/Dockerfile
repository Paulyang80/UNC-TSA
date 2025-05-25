# 使用 Python 3.11 作為基礎映像
FROM python:3.11-slim

# 設置工作目錄
WORKDIR /workspace

# 安裝基本工具
RUN apt-get update && apt-get install -y \
    git \
    curl \
    && rm -rf /var/lib/apt/lists/*

# 安裝 MkDocs 和常用插件
RUN pip install --no-cache-dir \
    mkdocs \
    mkdocs-material \
    mkdocs-git-revision-date-localized-plugin \
    mkdocs-minify-plugin

# 設置環境變量
ENV PYTHONUNBUFFERED=1

# 暴露 MkDocs 默認端口
EXPOSE 8000

# 設置默認命令
CMD ["mkdocs", "serve", "-a", "0.0.0.0:8000"]
