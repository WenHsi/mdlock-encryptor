# CLAUDE.md — MdLock 專案

此文件供 Claude 在協作此專案時參考，記錄架構決策、命名慣例與開發規則。

---

## 專案概覽

MdLock 是一組純前端工具，由兩個獨立 repo 組成：

| Repo | 功能 | URL |
|------|------|-----|
| `mdlock-encryptor` | AES-256-GCM 加密 Markdown + 上傳 GitHub Gist | https://wenhsi.github.io/mdlock-encryptor/ |
| `mdlock-viewer` | 即時 Markdown 預覽 + 解密閱讀 | https://wenhsi.github.io/mdlock-viewer/ |

每個 repo 各一個 `index.html`，單檔架構，無框架，無建構工具，無依賴。

---

## 命名規則

| 位置 | 正確寫法 |
|------|---------|
| 可見文字（title、h1、nav、og、meta） | `MdLock`、`Encryptor`、`Viewer` |
| nav logo HTML | `Md<em>Lock</em>`（em 保留 accent 色） |
| URL、repo 名稱、CSS class、JS 變數 | `mdlock-encryptor`、`mdlock-viewer`（kebab-case，全小寫） |

---

## 架構規則

### HTML 結構（每個 screen）
```
<nav>                        ← 全域導覽，不放 screen 專屬元件
  .nav-left > .nav-logo + .app-switch
  .nav-spacer
  全域按鈕（theme toggle、open/switch）
</nav>
<main>
  <div class="content-wrap"> ← max-width 容器，不用 flex/grid 縮窄
    screen 內容
  </div>
</main>
<footer>                     ← 在 content-wrap 外，全寬
```

### RWD 斷點
- 手機：`max-width: 767px`
- 桌面：`min-width: 768px`

### 手機版特殊元件
- `view-toggle-pill`（編輯/預覽切換）放在 `.mobile-editor .editor-copy-row`，**不放在 nav**
- `app-switch` 在手機版**不隱藏**，是關鍵導覽元素

### 外部連結
所有 `target="_blank"` 連結必須加 `rel="noopener noreferrer"`。

---

## CSS 變數（主題）

```css
--bg          背景
--surface     卡片/面板背景
--border      邊框
--text        主要文字
--text-muted  次要文字
--accent      品牌強調色（MdLock logo em 色）
```

---

## JavaScript 注意事項

- 程式碼設定 `.value =` **不會**觸發 `oninput` 事件，需手動呼叫相關更新函式
- GitHub Token 以 AES-256-GCM 加密後存入 `localStorage`（key: `enc_token`）
- 主題偏好存入 `localStorage`（key: `theme`）

---

## skill 檔案

開發規則整理於 `web-project-setup.skill`，包含：
- Rule 1：`<head>` 完整模板
- Rule 2：外部連結 `rel` 屬性
- Rule 3：footer safe-area padding
- Rule 4：表單驗證與 CRUD 回饋
- Rule 5：nav overflow 解法（pill 移出 nav）
- Rule 6：品牌名稱大寫規則
