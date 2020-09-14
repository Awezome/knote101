### Config
```
git config --global user.name "your name"
git config --global user.email "youremail@github.com"
```

### Branch
```
//本地分支
git branch
//查看远端分支
git branch -r
//切换分支
git checkout <branch-name>
//创建并切换到新建分支
git checkout -b <branch-name>
```

### Diff
```
//比较工作区与缓存区
git diff
//比较缓存区与本地库最近一次commit内容
git diff -- cached
//比较工作区与本地最近一次commit内容
git diff HEAD
```

### Ref.
https://juejin.im/post/6869519303864123399