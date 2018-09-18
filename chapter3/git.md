
**1. 安装**

```bash
# 创建密钥
ssh-keygen -t rsa -C "email"
git config --global user.name "name"
git config --global user.email "154...@qq.com"
```

**2. 基础命令**

```bash
git init
ls-ah                   # 查看隐藏文件
git add .               # 将文件添加到仓库
git commit -m "..."     # 本次提交说明
git status              # 当前仓库状态
git diff "fileName"     # 查看文件修改的内容 

git log --pretty=oneline    # 查看每条修改记录信息放在同一行
git reset --hard HEAD^      # 回退到上一个版本
git reset -- hard HEAD ~100 # 回退到前100个版本
git reset --hard "版本号"   # 回退到版本号的那个版本
```

**3. 关联远程仓库**

```bash
1. settings => ssh and GPG keys # 输入公钥
2. creat a new respository # 创建新仓库
3. git remote add origin git@github.com:hsiangleev/test.git # 关联远程仓库
4. git push origin master # 推送到远程库
5. git pull origin master # 拉取远程库
6. git clone git@github.com:hsiangleev/test.git # 克隆到本地
```

**4. 分支**

```bash
git branch                  # 查看分支
git branch "hsianglee"      # 创建分支
git checkout "hsianglee"    # 切换进入分支
git checkout -b "hsianglee" # 创建并切换分支
git merge "hsianglee"       # 合并某分支到当前分支
git branch -d "hsianglee"   # 删除分支
git log --graph             # 查看分支合并图
```

**5. 其它**

```bash
git remote -v                           # 查看远程库信息
git pull --rebase origin master         # 推送出错时
git push -u origin master -f            # 强制推送
```