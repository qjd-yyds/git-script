# git命令

#### 将工作区文件添加到暂存区

```javascript
git add <file>// 将单个文件添加到暂存区
git add . // 将所有文件添加到暂存区
```

#### 暂存区文件添加到git本地仓库

```javascript
git commit // 进入vim模式
git commit -m "描述" // 不进入vim模式
git commit -a -m "描述" // 合并add和commit
```

#### 删除文件

```javascript
git rm <filename> // 删除文件并从git管理删除
git rm -f <filename> // 	强制删除，可以删除被修改但是未提交文件
git rm -cache <filename> // 只删除暂存区 不删除工作区文件
```

#### 移动文件

```javascript
git mv <filename1.path> <filename2.path> // 将文件1的位置移动到文件2
```

#### 重命名文件名字

```javascript
/*
1.手动重命名
2. git rm <重命名之前到文件名>
3. git add <重命名之后的文件名>
*/ 
mv a.txt aa.txt // 将文件a.txt 改名为aa.txt 本质是删除原文件 创建新文件
/*
1.git 自动重命名
2.rm a.txt aa.txt
3.git rm a.txt
4.git add aa.txt
*/
```

#### 查看文件状态

```javascript
git status // 查看文件状态
git status -s // short简写，简化状态打印
```

#### 查看文件修改

```javascript
git diff // 查看工作区和暂存区的差异
git diff --staged // 查看暂存区差异
```

#### 查看日志

```js
git log
git log -p // 详细日志
git log --stat // 显示commit 和diff每个文件差异
git log -2 // 显示两个记录
git log --pretty=oneline // hash和描述
git log --pretty=short // hash和描述 作者
git log --pretty=full // hash和描述 作者 提交者
git log --pretty=fuller /// hash和描述 作者 提交者 日期
git log --pretty=format:"" // 定制显示的日志
git log --all --decorate --oneline --graph // all => 查看所有分支 oneline => hash描述 --graph 树桩可视化 decorate => 装饰每个提交指向分支 
git reflog // 查看历史提交的所有记录 用于回退等
```

#### 分支操作

```js
git branch // 查看本地分支
git branch <branchname>   // 创建分支
git checkout // 切换分支
git checkout -b <branchname> // 切换分支并创建
git branch -d <branchname> // 删除已经被合并的分支
git branch -D <branchname> // 强制删除分支
```

#### 分支合并

```js
git merge <barnchname> // 把目标分支合并到当前分支
// 快速前移概念(直接级祖先关系前移):
// 1.如果当前分支master的快照 a=>b=>c
// 2.合并的feature分支快照为a=>b=>c=>d 当前commit为 修改d.js
// 3.执行合并操作 git merge feature之后 不会生成merge的说明并且快速移动到feature的commit => 修改d.js
// 4.无法判断是合并操作还是master执行了commit操作

git merge --no-ff -m "合并操作 防止了快速前移 " feature // 消除了快速前移，并且commit变为 合并操作 防止了快速前移 

git merge --abort // 	执行合并操作后 发生冲突 ，用来取消合并
```

#### 撤销

```js
git checkout -- a.txt // 撤销没有被加入暂存区的a.txt 的修改
git reset HEAD a.txt // 取消暂存
git reset HEAD^ // 	撤销一次commit 有些编译器可能吧^ 看作换行 需要加上引号"HEAD^"
git reset HEAD^^ // 	撤销两次commit 几个^ 就是撤销几次
git reset HEAD~2 // 	撤销两次commit 	～后面可以接撤销几次
git reset [hash] // 	回退到hash值的commit
git reset --hard // 重置工作区，暂存区代码会丢失
git reset --soft // 保留工作区，和原分支差异存放至暂存
git reset --mixed（默认） // 保留工作区 清空暂存
git commit --amend // 当出现两次提交commit相同 合并提交
git commit -m "重置上一次修改的描述" --amend 	// 当上一次commit描述写错了 可以用这个来重置commit
```

#### 存储

```js
git stash // 存储工作区和其他暂存区未修改文件
git stash -u // 未追踪文件也被存储
git stash list // 查看存储的文件修改
git stash apply stash@{0} // 取出存储中的文件修改 不在暂存区 stash@{0} 为指定存储
git stash apply --index // 取出存储中的文件修改 放在暂存区
git stash drop 	// 	删除存储
```

#### 变基 

类似合并

```js
git rebase master // 变基的基础为master，提取当前feature分支和master分支非公共快照，切换master当执行git merge 实现快速master快速前移，
```

#### 远程仓库

```js
git remote add origin <url> // 链接本地仓库和远程仓库url
git push -u origin master // 提交远程仓库 master分支 并且后期提交自动提交远程master分支
git push // 提交代码当前分支到关联的远程分支
git clone <url> // 克隆项目到本地
git pull // 拉取代码
git checkout -b developer origin/developer // 远程克隆分支
git push origin :developer // 删除远程developer 分支
git push origin v0.0.1 // 提交一个标签
git push origin --tags //  提交所有标签
git push origin :refs/tags/v0.0.1 // 删除远程标签
```

#### 标签

```js
git tag v0.0.1 // 当前commit上 打上版本v0.0.1标签
git tag v0.0.2 hash // 给hash 对应的commit 打上0.0.2标签
git tag -a v0.0.3 -m "当前标签描述" hash // 给hash对应的commit 打上有描述的标签
git tag -d v0.0.2 // 删除标签
git show v0.0.3 // 查看当前版本的标签信息
```

