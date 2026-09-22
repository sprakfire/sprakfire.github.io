# 火線觀點 Fireline Perspective

用 [Hugo](https://gohugo.io/) + [Clarity 主題](https://github.com/chipzoller/hugo-clarity) 建置的個人網站，透過 GitHub Actions 自動部署到 GitHub Pages。

## 第一次上線

1. 在 GitHub 建一個新 repo。
   - 取名 `你的帳號.github.io` → 網址會是 `https://你的帳號.github.io/`
   - 取其他名字（例如 `fireline`）→ 網址會是 `https://你的帳號.github.io/fireline/`
2. 把這個資料夾的所有檔案推上去（包含隱藏的 `.github` 資料夾）：
   ```bash
   cd fireline-site
   git init
   git add .
   git commit -m "初始化網站"
   git branch -M main
   git remote add origin https://github.com/你的帳號/repo名稱.git
   git push -u origin main
   ```
   不想用指令也可以：在 repo 頁面按 **Add file → Upload files**，把整個資料夾內容拖進去。注意 `.github` 資料夾要一起上傳（macOS 按 `Cmd+Shift+.` 可顯示隱藏檔）。
3. 到 repo 的 **Settings → Pages**，把 **Source** 改成 **GitHub Actions**。
4. 到 **Actions** 分頁，等「Deploy Hugo site to Pages」跑完（約 1 分鐘）變成綠色勾勾，網站就上線了。

之後每次 push 到 `main`，網站都會自動更新。

## 待填的內容

搜尋 `TODO` 可以找到所有需要換成你自己資料的地方：

- `content/work-with-me.md`、`content/work-with-me.en.md`：Email、LinkedIn
- `content/podcast.md`：SoundOn、Spotify、Apple Podcasts 連結（也可以貼 SoundOn 嵌入播放器）
- `config/_default/menus/*.toml`：側欄社群連結
- `config/_default/params.toml`：大頭照
- `content/post/hello-fireline.md`：範例文章

## 寫新文章

```bash
hugo new content post/文章網址名稱.md
```

打開產生的檔案寫內容，寫完把 `draft: true` 改成 `false`，push 即可。

封面圖放在 `static/images/`，在文章開頭加 `thumbnail: "images/檔名.jpg"`。

要英文版就另存一份 `文章網址名稱.en.md`。

## 本機預覽

安裝 [Hugo extended](https://gohugo.io/installation/)（0.128 以上），然後：

```bash
hugo server
```

打開 http://localhost:1313/ 即可看到即時預覽。

## 綁定自訂網域

1. 在 `static/` 新增一個 `CNAME` 檔，內容只寫網域，例如 `firelineview.com`。
2. 在 repo 的 **Settings → Pages → Custom domain** 填入同一個網域。
3. 到網域商設定 DNS（GitHub 文件：Managing a custom domain for your GitHub Pages site）。

## 外觀調整

- 主色與字型：`assets/sass/_override.sass`
- 其他樣式：`assets/sass/_custom.sass`
- 主題本體在 `themes/hugo-clarity/`，建議不要直接改，要改就用上面兩個檔覆蓋。
