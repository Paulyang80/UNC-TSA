# UNC-TSA

一站式北卡羅萊納大學臺灣學生會（TSA）活動、資源與教學指南平台。

## 功能概覽

* **生活面**：當地住宿、交通、美食、購物等實用貼士。
* **學校面**：選課建議、校園設施介紹、學生社團資源。
* **教學面**：技術教學、常見問題、工作坊與教程連結。

## 專案結構

```text
unc-tsa-docs/             # 倉庫根目錄
├── .devcontainer/        # Dev Container 定義
│   ├── devcontainer.json
│   └── Dockerfile
├── docs/                 # MkDocs Markdown 原始檔
│   ├── index.md
│   ├── about.md
│   └── ...
├── mkdocs.yml            # MkDocs 全站設定
├── requirements.txt      # Python 套件列表
└── .github/workflows/    # 自動部署工作流程
    └── deploy.yml
```

## 前置需求

* 安裝 [Docker](https://docs.docker.com/)（若使用 Dev Container 或本地 Docker 版本）
* 安裝 [Git](https://git-scm.com/)
* 若要本地開發，可安裝 Python 3.8+ 並建立虛擬環境
* 推薦使用 VS Code + [Dev Containers](https://code.visualstudio.com/docs/devcontainers) 擴充

## 快速上手

### 1. 使用 Dev Container（推薦）

1. 於 VS Code 開啟本專案目錄。
2. 安裝並啟用 Dev Containers 擴充後，選擇「Reopen in Container」。
3. 容器啟動完成後，自動執行 `pip install -r requirements.txt`。
4. 在容器中執行：

   ```bash
   mkdocs serve --dev-addr=0.0.0.0:8000
   ```
5. 瀏覽器開啟 `http://localhost:8000/`，即可即時預覽並熱重載。

### 2. 本地開發

```bash
# 克隆倉庫
git clone git@github.com:<username>/unc-tsa-docs.git
cd unc-tsa-docs

# 建立並啟用虛擬環境
python3 -m venv venv
source venv/bin/activate

# 安裝套件
pip install --no-cache-dir -r requirements.txt

# 啟動 MkDocs 開發伺服器
mkdocs serve
```

預設監聽 `127.0.0.1:8000`，修改檔案後自動重載。

### 3. Docker 本地測試

```bash
# 建置映像
docker build -t unc-tsa-dev .

# 啟動容器並映射埠口
docker run --rm -it -p 8000:8000 unc-tsa-dev mkdocs serve --dev-addr=0.0.0.0:8000
```

## 自動部署

1. 推送至 `main` 分支後，GitHub Actions 會自動執行 `deploy.yml`。
2. 站點輸出至 `gh-pages` 分支，並由 GitHub Pages 提供內容。
3. 部署完成後，即可透過：

   > `https://<username>.github.io/unc-tsa-docs/`

## 客製化與進階

* **主題 & 樣式**：修改 `mkdocs.yml` 中 `theme` 參數，或放置自訂 CSS 至 `docs/assets/`。
* **多語系**：可整合 MkDocs Material 的國際化插件（i18n）。
* **搜尋與字彙**：安裝 `mkdocs-glossary-plugin`，為專業術語自動生成字彙表。

## 貢獻指南

1. Fork 本專案並建立 feature branch。
2. 編輯或新增 `.md` 文件並確認本地預覽正常。
3. 發起 Pull Request，並在描述中說明修改內容。

---

© 2025 UNC TSA Taiwanese Student Association
