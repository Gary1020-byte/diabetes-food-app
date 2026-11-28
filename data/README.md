# 台大美食地圖餐廳資料（NTUFOOD）

這是 diabetes-food-app 專案的餐廳資料來源，抓取日期 2026-11-25。

## 檔案

- `ntufood-restaurants.json` — 176 間餐廳，乾淨的 JSON 格式，可直接當作 `data/` 的種子資料。

## 資料來源

- 網站：https://www.ntufood.com/（NTUFOOD 台大美食隨機選擇器）
- 原始碼：https://github.com/pcwu2022/ntufood（公開 repo，24 顆星）
- 抓取的資料檔：https://www.ntufood.com/frontend/data.json（與 `frontend/data.js` 內容完全相同）
- 人工編輯的原始檔：`generate/data.csv`（repo 內）
- 線上編輯表：https://docs.google.com/spreadsheets/d/1k7IUK_FrCZbTatBzo8tfCVHp7Xrc1764eFq2fBQuScg/edit?usp=sharing
- 創作者：Po-Chun Wu（pcwu2022）、Eric Yeh（ergs0204）

網站本身只用靜態資料檔，沒有 API；後端（ntufood-backend.onrender.com）只負責瀏覽／點擊統計和熱門推薦，不提供餐廳清單。

## 欄位說明

| 欄位 | 說明 |
|---|---|
| `id` | 本檔案內的編號（`ntufood-001` 起） |
| `name` | 店名（原始 `Restaurant`） |
| `location` / `location_zh` | 區域代碼與中文（公館、118 巷、新生南路、校內、六張犁、師大、台科大、醫學院） |
| `genre` / `genre_zh` | 類別代碼與中文（共 25 種，便當、日式、拉麵、中式、麵店最多） |
| `price` | 價位 1–5（網站上的 🪙 數量）；4 間沒有價位，記為 `null` |
| `tags` | 標籤陣列：`OnePerson` 一個人吃、`Gathering` 多人聚餐、`Dating` 適合約會、`FastServe` 快速上菜、`SlowEat` 慢慢吃（原始資料標 `O` 才算有） |
| `latitude` / `longitude` | 座標（原始 `Coordinates` 字串拆開的數字） |
| `google_maps_url` | Google Maps 搜尋連結（依網站 script.js 的格式產生） |
| `comments` | 備註；只有 2 間有內容（義樂義大利麵、燒肉政宗-中正店，都是學生證優惠） |

`location_labels`、`genre_labels`、`tag_labels` 三個對照表也放在同一個 JSON 裡，App 可以直接用。

## 資料品質注意事項

- 全部 176 間都有座標；網站自己有註明「地圖位置不一定準確」。
- 「翊芳庭生活館」在原始資料出現兩次（便當／早餐，同一個點），兩筆都保留原樣。
- 價位分布：1 級 49 間、2 級 81 間、3 級 24 間、4 級 14 間、5 級 4 間、無價位 4 間。
- 區域分布：公館 75、118 巷 55、新生南路 24、校內 15、師大 3、六張犁 2、台科大 1、醫學院 1。

## 授權注意事項（重要）

- 原始 repo（pcwu2022/ntufood）**沒有 LICENSE 檔案**，這份資料不在任何開放授權之下。
- 已獲作者授權：Po-Chun Wu 於 2026-11-25 回信同意直接使用這份資料（專案用途，標註 NTUFOOD／ntufood.com 來源，不再散布）。
- 作者已不在台大，若無使用者建議，資料不會再更新；App 與企劃書不應聲稱資料會持續更新。
- 餐廳名稱與座標是事實性資料，但整份清單是作者整理的成果，引用時請標註來源。

## 更新方式

資料有變時，重新下載 https://www.ntufood.com/frontend/data.json，照同樣的欄位規則轉換即可；或直接看 repo 內的 `generate/data.csv` 是否有更新。
