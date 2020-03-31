## 项目分支介绍

- 主分支`master`

- 预生产分支`pre`

- 测试分支`test`

- 功能分支`feature/版本号`

- 修复分支`hotfix/xxx`

  

## git开发流程

无论是开发新功能还是修复线上bug都需遵循以下步骤及规范

1. 从`master`切一个新分支

   ```js
   // 切到master分支
   git checkout master
   
   // 拉取最新代码
   git pull --rebase
   
   // 切一个新的分支，功能分支起名「feature/版本号」，修复分支起名「hotfix/版本号」
   git checkout -b feature/111
   ```

   

2. 多人开发同个功能分支时

   ```
   // 当远程的提交多于本地提交时，一定要
   git pull --rebase
   再
   git push
   ```

3. 功能开发完毕，提测

   ```
   // 切到test分支
   git checkout test
   
   // 拉取test代码
   git pull --rebase
   
   // 合并功能分支
   git merge feature/111
   
   // push到远程
   git push
   ```

4. 发布预生产，步骤同3

   ```
   // 切到pre分支
   git checkout pre
   
   // 拉取pre代码
   git pull --rebase
   
   // 合并功能分支
   git merge feature/111
   
   // push到远程
   git push
   ```

5. 测试通过后，需要rebase 最新的 `master` 分支

   ```
   // 切到master分支
   git checkout master
   
   // 拉取最新master代码
   git pull --rebase
   
   // 再切到当前开发的分支
   git checkout feature/111
   
   // rebase master
   git rebase master
   
   // 如果rebase 产生冲突，手动解决冲突，然后
   git add .
   git rebase --continue
   
   // rebase 完之后，强push到远程
   git push --force-with-lease
   	
   ```

   

6. 在gitlab 上提一个MR (merge request)，让负责人合并代码