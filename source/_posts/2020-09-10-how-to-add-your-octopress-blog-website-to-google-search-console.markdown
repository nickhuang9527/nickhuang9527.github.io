---
layout: post
title: "如何使Octopress website能被Google搜索到"
date: 2020-09-10 23:29:22 +0800
comments: true
categories: [Octopress]
---

1. 登入[Google search console](https://search.google.com/search-console/welcome)
2. 選擇```網址前置字元```
3. 提交Blog的Domain name```http://[username].github.io/```
4. 下載驗證的html檔案
5. 放到```octopress/source```目錄下
6. 建置及部署
	```
   rake gen_deploy
   ```
7. 回到Google search console，點擊驗證，完成
   
   