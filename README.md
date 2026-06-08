# MdLock Encryptor

AES-256-GCM 加密 Markdown，上傳 GitHub Gist，產生加密分享連結。純前端，無後端，無伺服器。

🔗 **Live** → https://wenhsi.github.io/mdlock-encryptor/

---

## 功能

- **AES-256-GCM 加密**：瀏覽器本地執行，密碼不離開裝置
- **GitHub Gist 上傳**：加密後的密文直接存入 Gist，取得分享連結
- **一鍵產生閱讀連結**：自動組合 MdLock Viewer URL + Gist ID
- **即時 Markdown 預覽**：編輯與預覽同步，支援桌面分割畫面
- **深色 / 淺色主題**：偏好設定儲存於 localStorage
- **完整 RWD**：桌面分割編輯、手機單欄切換

---

## 使用方式

1. 開啟頁面，首次使用輸入 GitHub Token 並設定密碼鎖定
2. 在編輯區撰寫 Markdown
3. 填入加密密碼，點擊「加密並上傳 Gist」
4. 複製產生的閱讀連結，分享給對方
5. 對方在 MdLock Viewer 輸入相同密碼即可閱讀

---

## 技術

| 項目 | 說明 |
|------|------|
| 加密 | Web Crypto API — AES-256-GCM |
| 金鑰派生 | PBKDF2（SHA-256，100,000 次迭代） |
| 上傳 | GitHub Gist API v3 |
| 架構 | 純 HTML / CSS / JS，單檔，無框架，無依賴 |

---

## 相關

- [MdLock Viewer](https://wenhsi.github.io/mdlock-viewer/) — 閱讀加密文件

## License

MIT © 2026 wenhsi
