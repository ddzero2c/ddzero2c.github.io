---
title: '使用 Hugo 來建立這個部落格網站'
date: 2023-01-21T02:39:28+08:00
draft: true
tags:
  - hugo
  - githubpage
---

## 目標

- 文章可以用 markdown 編輯
- 文章可以根據 tag 做分類
- 串接 Google Analytics
- 擁有自己的網址

## 先決條件

- 作業系統：macOS
- 下載 [Hugo](https://gohugo.io/): `brew install hugo`
- 你已經會使用 `git`

## 建立部落格

```bash
hugo new site blog
cd blog
git init
git submodule add https://github.com/monkeyWzr/hugo-theme-cactus.git themes/cactus
echo "theme = 'cactus'" >> config.toml
hugo server -D
```

打開 [http://localhost:1313](http://localhost:1313) 就能看見部落格首頁囉！

大部分主題都有附上 Github 的連結，
並且有一個 [`exampleSite/config.toml`](https://github.com/monkeyWzr/hugo-theme-cactus/blob/main/exampleSite/config.toml) 目錄來教你如何設定 `config.toml`，
例如你可以會想要修改標題：

```toml
baseURL = "https://example.com"
languageCode = "en-us"
theme = "cactus"
title = "我的部落格"
copyright = "我是誰"
```

儲存檔案後回到網頁上，應該就能看到網頁名稱變成了 "**我的部落格**"。其他的設定就自行摸索囉！

接著來建立第一篇貼文： `hugo new content/posts/use-hugo-to-build-this-blog.md`

打開 `content/posts/first-post.md` 你會看到

```markdown
---
title: '使用 Hugo 來建立這個部落格網站'
date: 2023-01-21T02:39:28+08:00
draft: true
tags: # 請自行添加 tag, hugo 會幫你在首頁上分類文章
  - hugo
---
```

當你寫完文章時請將 `draft` 改為 `false`, 並重新執行 `hugo`
這樣就發布完成啦！

## 設定網站

以上都是在你的電腦上執行 hugo 來協助你編輯文章  
接下來我們要將整個部落格放到網頁上

首先，你需要在 GitHub 上建立一個新的 repository，命名為 yourusername.github.io，其中 yourusername 是你的 GitHub 用戶名。
接著，在你的部落格目錄下，執行以下指令：

```bash
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/yourusername/yourusername.github.io.git
git push -u origin main
```
