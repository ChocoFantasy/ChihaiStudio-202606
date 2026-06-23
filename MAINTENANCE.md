# 千海映畫首頁維護規格

## 1. 專案概述
這是一個單頁靜態網站，使用 Bootstrap 5 建構。頁面內容包含：

- LOGO 與網站導覽
- 漢堡按鈕選單（右上展開）
- 五張輪播圖
- 關於區塊（左圖右文）
- 服務案例卡片
- 頁尾資訊
- 固定右下「回到頂端」按鈕

## 2. 資料夾結構
```
/ (根目錄)
  index.html
  MAINTENANCE.md
  /css
    bootstrap.min.css
    style.css
  /js
    bootstrap.bundle.min.js
  /images
    01.png
    02.png
    03.png
    04.png
    漢堡按鈕.png
```

## 3. 主要檔案說明

### `index.html`
首頁主檔案，包含整個頁面結構與內容。

重點區塊：
- `header`：LOGO、導覽列、漢堡按鈕
- `#homepageCarousel`：輪播圖區塊
- `#about`：關於千海映畫稿
- `#service`：服務案例卡片
- `footer`：聯絡資訊、社群連結
- `#backToTop`：固定回頂按鈕

### `css/style.css`
自訂樣式檔，所有專案自定義 CSS 都集中放在這裡。

包含：
- 文字、標題、卡片樣式
- 漢堡選單樣式
- 回到頂端按鈕樣式
- 固定右上漢堡開關定位

### `js/bootstrap.bundle.min.js`
Bootstrap 5 的 JavaScript bundle，用於啟用輪播、offcanvas 和其他互動元件。

## 4. 波浪輪播圖維護

目前輪播圖使用外部 Unsplash 連結。若要改成本地圖片：

1. 將圖片放到 `/images` 資料夾
2. 在 `index.html` 裡 `#homepageCarousel` 的 `img src` 屬性改成 `images/檔名.png`

建議使用 1200px 寬度以上、長寬比 16:9 或接近 1.8 的海浪照片。

## 5. 漢堡選單維護

漢堡選單按鈕現在使用 CSS 製作三條線圖案，位於右上。點擊後會開啟 `#mobileMenu` offcanvas。

如果要調整選單內容，編輯 `index.html` 中：

```html
<div class="offcanvas-body">
  <div class="menu-card">
    <a href="#about">關於千海</a>
    ...
  </div>
</div>
```

如果要調整按鈕位置或樣式，編輯 `css/style.css` 中的 `.navbar-toggler` 和 `.hamburger`。

## 6. 回到頂端按鈕

按鈕元素為：

```html
<button id="backToTop" class="back-to-top" aria-label="回到頂端">
  <i class="bi bi-arrow-up-short"></i>
</button>
```

行為在 `index.html` 底部透過以下 JS 控制：

```js
window.addEventListener('scroll', toggle);
btn.addEventListener('click', function(){ window.scrollTo({ top: 0, behavior: 'smooth' }); });
```

## 7. 頁面預覽與驗證

建議使用本機靜態伺服器預覽，避免直接從檔案系統打開導致路徑或快取問題。

可以用簡易命令：

```bash
cd d:\website
python -m http.server 8000
```

然後用瀏覽器開啟 `http://localhost:8000`。

## 8. 備註

- `bootstrap-icons` 目前仍使用 CDN 連結；若希望離線維護，可新增本地 icon 檔案並改成本地引用。
- 若要新增其他頁面，可複製 `index.html` 並修改內部連結。
- 若要把輪播改為本地圖片，請同步更新 `images` 內檔名與 `index.html`。
