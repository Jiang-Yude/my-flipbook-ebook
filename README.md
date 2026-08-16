# 翻頁電子書套版 · Flipbook Demo

把一疊 1:1 正方形圖片，套成一本可以翻的電子書網頁。真實頁角捲曲翻頁效果，手機、電腦都能操作。

**線上 Demo**：https://jiang-yude.github.io/my-flipbook-ebook/

## 特色

- **真實翻頁**：滑鼠移到頁角會捲起，拖著頁角翻頁（StPageFlip 引擎，已內建、離線可用）。
- **多種操作**：滑鼠拖曳、點頁面、方向鍵 ← →（按住連翻）、上下頁按鈕。
- **手機電腦通用**：電腦攤開跨頁，手機直向自動切單頁、左右滑動。
- **三種頁型**：滿版照片頁、地點介紹頁（照片＋地點＋文字）、可互動 Google 地圖頁（可縮放點選）→ 旅遊故事書。

## 怎麼換成自己的內容

1. 把自己的圖片（1:1 正方形，建議 900×900、JPG）放進 `images/`，檔名 `page-01.jpg`、`page-02.jpg`⋯依順序，第一張是封面。
2. 打開 `index.html`，改最上面的 `PAGES` 陣列。三種頁型語法：

```js
{ type: 'image', src: 'images/page-01.jpg' }                        // 滿版照片頁
{ type: 'story', img, title: '大標', location: '國家 · 城市', text: '短介紹' }  // 地點介紹頁
{ type: 'map',   title: '這一站：XXX', query: '地點名', note: '提示' }          // Google 地圖頁
```

3. 順手改 `<title>`、頁面上方標題、封面左側標題區文字。
4. 用瀏覽器打開 `index.html` 就能看。

## 檔案結構

```
index.html                  ← 整本書（HTML/CSS/JS 都在這）
images/                     ← 你的圖片
vendor/page-flip.browser.js ← 翻頁引擎（StPageFlip，離線可用）
```

## 授權

翻頁引擎 [StPageFlip](https://github.com/Nodlik/StPageFlip) 為 MIT 授權。Demo 圖片為 [Lorem Picsum](https://picsum.photos) 佔位圖。

## 音樂翻頁電子書（music-flipbook.html）

同一本書配一首歌，一頁一段歌詞。讀者按播放聽歌、自己翻頁，翻到哪一頁就顯示那一段歌詞。

- **不自動翻頁**（2026-08-16 定案）。
- 要改的只有檔案最上方兩個常數：`SONG_URL`（音檔網址）與 `LYRICS`（一格一頁的歌詞陣列）。
- 音檔開發期可直接吃 SUNO 分享頁背後的 mp3（`cdn1.suno.ai/<id>.mp3`，有開 CORS）；交付版建議下載放進 `audio/`。
- 錄音旁白版與時間軸自動翻頁版已移除，要找在 commit `6c99e72` 之前的歷史。
