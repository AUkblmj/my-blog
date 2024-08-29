---
title: git上传超过100MB大文件
date: 2024-08-21 22:54:38
author: AUkblmj
---

> 下载 [git-lfs]([Releases · git-lfs/git-lfs (github.com)](https://github.com/git-lfs/git-lfs/releases?utm_source=gitlfs_site&utm_medium=releases_link&utm_campaign=gitlfs))

> 进入安装后的目录，打开gitBash，执行`git lfs install`

> 到达仓库目录，打开gitBash

```bash
git init
git lfs track 大文件
git add .gitattributes
git commit -m "pre"
git remote add origin git@github.com:AUkblmj/source.git
git branch -M main
git push -u origin main 
git add -f 大文件
git commit -m "上传大文件"
git push origin main
```

