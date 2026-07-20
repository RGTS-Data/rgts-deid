# rgts-deid — 去識別化工具 (De-identification tool)

純前端（client-side）敏感資訊遮蔽工具。**所有處理都在你的瀏覽器內完成，檔案不上傳、不留存、可離線使用。**

A privacy-first, fully client-side redaction tool. Nothing is uploaded — every file is processed locally in your browser.

---

## 功能 Features

- **文字 Text** — 貼上文字，自動偵測並遮蔽：
  - 公司名 · 客戶名 · 專案號 · 型號/序號 · 金額 · Email · 電話 · 身分證 · 統編 · 信用卡 · IP/MAC · 地址 ＋ 自訂字典
  - 4 種遮蔽方式：**塗黑** / **類別標籤** / **一致假名** / **雜湊**
- **圖片 Image** — 上傳截圖或照片 → 拖曳框選 → **塗黑 / 模糊 / 馬賽克** → 匯出 PNG
- **文件 Document** — 直接上傳 **Word (.docx) / PowerPoint (.pptx)**（純前端解壓）→ 偵測遮蔽 → 還你**同格式、保留排版**的遮蔽檔；純文字 (.txt) 亦可。**PDF 與照片內文字/人臉為下一版。**

## 使用 Usage

下載 [`index.html`](./index.html)，用瀏覽器打開即可 — 不需安裝、不需連線。
亦可部署到任意靜態主機，或用 Edge / Chrome「安裝」成桌面 App（PWA，開發中）。

## 隱私 Privacy

- 沒有後端、沒有追蹤、不呼叫外部 API 處理你的內容
- 純 `index.html` 單檔，可離線 / 內網使用
- 適合對外分享文件前，先清掉客戶名、專案號、個資

## Roadmap

- [x] 文字偵測引擎（公司/客戶/PII…）＋ 圖片手動框遮蔽
- [x] 文件上傳：**Word (.docx) / PowerPoint (.pptx)** — 零依賴解壓→遮蔽→同格式下載（保留排版）
- [ ] 文件上傳：**PDF** — pdf.js render + 座標塗黑 + 攤平成不可反選
- [ ] 照片內文字 OCR ＋ 人臉自動偵測（含 PDF/Word/PPT 內嵌照片）
- [ ] PWA 離線安裝（Windows / Mac 桌面 App）
- [ ] 客戶名字典接 D1 `customers` 自動帶入

> ⚠️ 已知限制：Word/PPT 的敏感詞若被拆成多個 run（同一詞跨格式片段）目前逐 run 偵測，可能漏抓；多數欄位（email/電話/公司名）落在單一 run，實務命中率高。跨 run 合併偵測為後續改進。

## 授權 License

[MIT](./LICENSE)
