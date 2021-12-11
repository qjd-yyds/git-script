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
```

