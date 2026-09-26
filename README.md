# 花光光收單系統

全客製化花藝的線上收單系統。客人在前台填寫需求，花藝師在後台用月曆管理訂單。

- **前台（客人填單）**：`index.html` — 姓名、電話、面交日期／時間／地點、預算、風格描述、參考圖片（1 張）
- **後台（花藝師）**：`admin.html` — Email 登入、月曆總覽（每日訂單數與預算合計）、訂單詳情、狀態更新

訂單狀態：待確認 → 客人已付款 → 製作中 → 已完成

## 技術

- 純 HTML / CSS / JavaScript，部署於 GitHub Pages
- 資料庫、圖片儲存、登入皆使用 Supabase（Database / Storage / Auth）

## 資料安全

- 前端只包含 Supabase 的 publishable key，這把金鑰設計上就是公開的。
- 資料權限由 Supabase Row Level Security 控管：
  - 未登入：只能新增訂單、上傳參考圖片，無法讀取或修改任何訂單
  - 管理員（列於 `admin_users`）：可讀取訂單、查看圖片、更新狀態
