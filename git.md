
**由于代码重合导致的push失败，需要先拉取远程分支再合并**
```shell
git stash
git pull ... 
git stash pop
```
---


**删除不想要的远程分支main(注意 main必须非默认分支)**
```shell
git  push -f  origin  --delete main
```
---


**想要全部清空并更新到最新代码，不保留本地修改**
```shell
git fetch origin 
git clean -f 
git reset --hard origin/master #可以是指定的版本
```
---


**commit后还没push，想要修改commit的信息**
```shell
git commit --amend
```
---


**commit后已经push了，但是还想改之前commit的信息**
```shell
git log --oneline    #通过这个找到对应的SHA-1 校验和
git checkout <commit-SHA>
git commit --amend
git push --force origin <branch-name>
```
---


**提交子项目的修改内容**

    ①进入子项目          cd child_project/  
    ②添加修改的文件      git add modified_file.txt  
    ③提交修改的标题      git commit -m "Added new feature to subproject"  
    ④推送到子项目上      git push origin master  
    ⑤进入主项目          cd main_project/  
    ⑥添加修改的子项目    git add child_project  
    ⑦提交修改的标签      git commit -m "Added new feature to project"  
    ⑧推送到主项目        git push origin master  
---


**报错：error: src refspec xxx does not match any / error: failed to push some refs to解决**
该问题是由于本地分支和push分支无法关联，可以将本地分支名改成远程push分支名即可

---


**撤销对子项目的修改**
```shell
git submodule foreach --recursive git checkout .
```
---


**删除子项目目录并重新拉取分支**
```shell
rm -r {submoudle_path}
git submodule update --init --recursive
```
---

**将本地git仓库a的代码合入到远程git仓库b中**
```shell
git remote add upstream git@git@github.com:xxx/b.git
git fetch upstream
git checkout main
git merge upstream
#解决合并后的冲突
git add .
git commit -m "xxx"
git push upstream main
```
---

