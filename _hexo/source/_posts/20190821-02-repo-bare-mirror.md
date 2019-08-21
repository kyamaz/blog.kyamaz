---
title: Github の private repository への bare & mirror 
date: 2019-08-21 20:30:00
tags: misc
mathjax: true
---

本開発は, 暫くはステルスで開発しております.  公開されている repository を元にしていますが, fork した repository ではなく, 
次の手順で非公開（ Private ）の repoository に bare & mirror して開発を進めます.  

```
# あらかじめ, 同名の空のリポジトリを非公開（ Private ）として作成しておきます. 
export SYNC_MODULE=risv-tools

git clone --bare --config remote.origin.fetch='+refs/heads/*:refs/heads/*' --config remote.origin.mirror=true https://github.com/riscv/${SYNC_MODULE}.git
cd ${SYNC_MODULE}.git
git remote add --mirror=push other https://openql-org@github.com/openql-org/${SYNC_MODULE}.git
git push other
```

