## git上传至远程仓库步骤

git 官方指令：

```powershell
echo "# 1" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/wjz09/114514.git
git push -u origin main
```



猜的步骤：

```bash
git init #本地仓库初始化

git add filename #文件添加至暂存区,支持多次添加

git commit -m “描述”  #提交文件到仓库

git remote add 仓库名 git地址

git push -u 仓库名 master 

·······································································

更新：

git add
git commit 
git push

```

## git下载指定分支文件：

示例文件夹连接：

```bash
https://github.com/PowerShellEmpire/PowerTools/tree/master/PowerView
```

将/tree/master/ 替换为 /trunk/ 

在下载文件夹右键 **SVN checkout**，导入修改后的url，下载。