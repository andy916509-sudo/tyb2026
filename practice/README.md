# 分部練習室

管樂分部練習工具：看分譜、聽音樂、調速度、框選循環、和其他聲部合奏。

## 兩種放樂譜的方式

1. **在網頁上直接加入**（最簡單）
   按「📂 我的樂譜 → ＋ 加入樂譜檔」，選 `.musicxml`／`.xml`／`.mxl`。
   檔案只存在那台裝置的瀏覽器裡，別人看不到。

2. **放進網站給全團用**
   把 MusicXML 檔放到 `scores/` 資料夾，然後在 `scores/manifest.json` 登記：

   ```json
   {
     "songs": [
       {
         "title": "曲名",
         "parts": [
           { "name": "Flute 1", "file": "曲名-Fl1.musicxml" },
           { "name": "Clarinet 2", "file": "曲名-Cl2.musicxml" }
         ]
       }
     ]
   }
   ```

   同一首曲子的聲部放在同一個 `parts` 清單裡，就能在「合奏」一起播放。

## 匯出 MusicXML

- MuseScore：檔案 → 匯出 → MusicXML（分譜可勾選「各聲部分別匯出」）
- Sibelius／Finale／Dorico：匯出 → MusicXML

## 上線

整個 `practice/` 資料夾是純靜態網頁，可直接部署到 Vercel 或 GitHub Pages（根目錄設為 `practice`）。
本機測試：在 `practice/` 裡執行 `python3 -m http.server`，打開 http://localhost:8000 。

## 目前限制

- 反覆記號、D.S.、Coda 不會自動跳，依樂譜順序直線播放。
- 打擊樂（無音高）用簡單的合成聲音代替。
