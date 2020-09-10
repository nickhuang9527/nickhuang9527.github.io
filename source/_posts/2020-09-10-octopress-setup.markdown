---
layout: post
title: "使用Octopress架設靜態Blog"
date: 2020-09-10 23:18:16 +0800
comments: true
categories: [Octopress] 
---

## 為什麼要寫Blog?
工作中受到了很多教學網站及博客文章(簡書, CSDN, Medium...)非常多的幫助，因此想寫部落格將自己學到的技術記錄下來，一方面讓自己複習，一方面也希望能幫助到有需要的人。

## 為什麼用Octopress?
其實有很多現成免費的部落格平台像是Medium, Blogger等...，但最後我還是決定用Octopress來建立自己的部落格，它吸引我的原因如下:

1. 使用Git做版本控管，託管於Github
2. 使用Markdown寫文章
3. 可以學到東西
4. 免費

Git對軟體工程師再熟悉不過了，且託管於工程師最愛充滿開源專案的Github平台，用Markdown寫文章，也能訓練自己寫README語法的熟練程度，又可以學到東西，因此選擇Octopress。

## 事前準備

- 申請[Github](https://github.com)帳號
- 安裝[Git](https://git-scm.com) 

```
brew install git
```
- 安裝[Ruby](https://www.ruby-lang.org/zh_tw/documentation/installation/)

```
brew install ruby
```
確認版本

```
ruby --version
```

## 建置Octopress
```
git clone git://github.com/imathis/octopress.git octopress
cd octopress
```
安裝依賴

```
gem install bundler
rbenv rehash    # If you use rbenv, rehash to be able to run the bundle command
bundle install
```
安裝Octopress預設主題

```
rake install
```
## Github page
[Github page](https://pages.github.com)提供我們免費架設靜態網站，雖然有些限制(Ex: 沒有DB, Server配置等...)，但非常簡易就能部署，非常適合用來做個人部落格。

1. 到[Github](https://github.com)申請一個帳號
2. 建立一個repository，命名為[username].github.io，[username]為你Github的用戶名，請務必要用此格式命名，不然後面會無法部署。

完成後會看到一個ssh URL
```
git@github.com:username/username.github.io.git
```
，這就是你的遠端repository位置

## 部署到Github page

- 設置Github page repo位置

```
rake setup_github_pages
```

此時會要你輸入github page的位置，還記得上面建立完成後所產生的ssh URL，複製並輸入

```
git@github.com:username/username.github.io.git
```
- 產生及部署部落格

```
rake generate
rake deploy
```

上面指令會產生出你的部落格，並把產生的檔案複製到```_deploy/```資料匣中，並把它們加入git中，commit及push到master branch。

到這裡你可以先在Browser打開http://[username].github.io/，就可以看到你的部落格囉!

最後別忘記將source commit並push到遠端的repo

```
git add .
git commit -m 'your message'
git push origin source
```

## 發布文章

所有的文章必須放在```source/_posts```目錄下

- 創建新文章

```
rake new_post["title"]
```

此時在```source/_posts```目錄下會產生一個```YYYY-MM-DD-post-title.markdown```的檔案，我們就可以打開檔案開始寫部落格了

```
cd source/_posts/
vim YYYY-MM-DD-post-title.markdown
```

也可用其他編輯器開啟寫文章，像是: [MacDown](https://macdown.uranusjr.com)等...

寫完文章後再執行前面提到的***產生及部署部落格***

```
rake generate
rake deploy
```

or 

```
rake gen_deploy
```

最後再將剛所寫的文章加入commit，並push到遠端的repo

```
git add .
git commit -m 'your message'
git push origin source
```

## 總結
Octopress基礎建置就到這邊，未來如果有時間會再深入研究更多Octopress的新功能，寫成文章分享給大家!
