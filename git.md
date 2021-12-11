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
```

#### 分支操作

```js
git branch // 查看本地分支
git branch <branchname>   // 创建分支
git checkout // 切换分支
git checkout -b <branchname> // 切换分支并创建
```

#### 分支合并
