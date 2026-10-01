# Media Assets

本儲存庫以 **公開 GitHub Issue 附件** 保存網站、文章與文件使用的圖片。Git 分支只保存 README、文字規範及來源 metadata。

## Agent 必讀規則

- **圖片只上傳至 Issue 本文或 comment 的附件。不得將圖檔提交到 main、master 或任何工作分支。**
- 不使用 Git blob、Contents API、commit、push、Git LFS、Release 或其他分支代替 Issue 附件；也不以「來源」、「原圖」或「備份」為由另存一份到 Git。
- 在 Issue 貼上原站網址或 `raw.githubusercontent.com` 網址只是引用圖片，**不代表已上傳 GitHub 附件**。
- 圖檔下載與上傳前的暫存放在 Git 外；Git 只記錄原始來源網址、語意化檔名、SHA-256、尺寸、用途、alt、Issue 與實際附件網址。
- 遇到未登入、CLI 版本或權限限制時，回報限制並保留來源紀錄；取得可用上傳方式後再保存，不改為提交圖檔。
- `.gitignore` 排除圖片格式；Agent 仍須檢查提交差異，不得使用 `git add -f` 繞過規則。

## 正確使用流程

1. 先找同一篇文章或同一使用單位的既有 Issue。沒有時建立一個；多張圖片共用該 Issue。
2. 使用穩定 Asset ID，例如 `article-template/rocket-example`，在 Issue 本文或 comment 記錄用途、原始來源、取得日期、語意化檔名、SHA-256、Content-Type、大小、原始尺寸及 alt。
3. 在 Issue 編輯區拖曳、貼上或選擇圖片，等候 GitHub 完成上傳；也可使用支援 `--attach` 的官方 GitHub CLI。
4. 複製 GitHub **實際產生**的完整附件網址，保存到 Issue 索引及使用端 manifest，並用於 Markdown 或 HTML 的圖片引用。不要自行拼接 UUID。
5. 未登入下載附件，核對 Content-Type、尺寸、SHA-256 及顯示結果，再更新使用端。
6. 更換內容時上傳新附件、更新引用，保留來源及版本紀錄。不要刪除仍被引用的 Issue 或附件。

Issue 標題建議使用 `YYYY-MM-DD | 專案 | 內容識別碼 | 資產集合類型`。日期為首次建立日；後續補圖保留日期。

## 瀏覽器與官方 CLI

瀏覽器：開啟 Issue 本文或 comment 編輯區，上傳圖片後取得網址，例如：

```markdown
![能表達圖片資訊的替代文字](https://github.com/user-attachments/assets/<GitHub 實際產生的 UUID>)
```

官方 GitHub CLI 2.99.0 起提供附件功能；使用前以 `gh issue edit --help` 確認支援。原圖放在 Git 外的暫存目錄，於該目錄執行：

```powershell
gh issue edit ISSUE_NUMBER --repo SyuanTsai/Media-Assets --attach ./image.png
```

搭配正文檔案可保留來源 metadata 及 alt；正文內的本機圖片引用會由 CLI 改成已上傳的附件網址：

```powershell
gh issue edit ISSUE_NUMBER --repo SyuanTsai/Media-Assets --body-file ./asset-record.md --attach ./image.png
```

CLI 上傳需要已授權且具有 Repository 寫入權限的帳號。這項權限不表示可以提交圖檔；附件上傳與 Git 寫入是不同操作。附件尚未可讀時先等候並重驗，不以 Git 圖片替代。

## 既有資產與使用端

- [Issue #1：文章範本火箭](https://github.com/SyuanTsai/Media-Assets/issues/1)
- [Issue #3：詛咒深淵平衡性公告](https://github.com/SyuanTsai/Media-Assets/issues/3)
- [Issue #4：溢洪道公告](https://github.com/SyuanTsai/Media-Assets/issues/4)
- [Issue #5：1.13.0 更新公告](https://github.com/SyuanTsai/Media-Assets/issues/5)
- [Issue #6：老兵五個天賦圖示](https://github.com/SyuanTsai/Media-Assets/issues/6)

[附件 metadata 對照](records/attachments.json)只保存文字紀錄。2026-10-01 已將主分支的 26 張圖檔移除，公告圖片及技能圖示改用附件；本次清理保留原有 Git 歷史。

使用端包括 [DARKTIDE 文件](https://github.com/SyuanTsai/Warhammer-40-000-DARKTIDE-Mods)與[個人網站](https://github.com/SyuanTsai/SyuanTsai.github.io)。使用端只記錄 metadata 與附件 URL，不另提交這些圖片作 Git 備份。

## 來源與權利紀錄

附件保存方式不改變圖片的權利。原始來源、作者、授權及修改紀錄依每個 Issue 的證據記錄；遊戲圖片權利仍歸原權利人，本儲存庫不另授權。

既有火箭圖片的「User-provided」標籤未證明其原始來源或再散布權；移除 Git 圖檔不解除這項來源缺口。保留既有附件紀錄，不新增或推定授權。詳見 [ASSET-PROVENANCE.md](ASSET-PROVENANCE.md)、[LICENSE-SCOPE.md](LICENSE-SCOPE.md)、[THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)及 [LICENSES/NO-ADDITIONAL-LICENSE.md](LICENSES/NO-ADDITIONAL-LICENSE.md)。

GitHub 附件操作參考：[瀏覽器附件說明](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/attaching-files)、[官方 CLI 附件說明](https://docs.github.com/en/github-cli/github-cli/attaching-files-with-github-cli)。
