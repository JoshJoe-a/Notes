# Notes
##### 一、fnm 常用命令及使用场景

###### 1.安装 Node 版本

- **安装指定版本**：
  `fnm install <版本号>`
  示例：`fnm install 18.16.0`
- **安装最新 LTS 版本**：
  `fnm install --lts`
- **安装最新稳定版**：
  `fnm install latest`

###### 2. 版本切换

- **临时切换版本**（仅当前终端生效）：
  `fnm use <版本号>`
  示例：`fnm use 20.0.0`
- **设置默认版本**（全局生效）：
  `fnm default <版本号>`
  示例：`fnm default 18.16.0`

###### 3. 版本管理

- **列出已安装版本**：
  `fnm list`
- **列出远程可用版本**：
  `fnm list-remote`
- **卸载指定版本**：
  `fnm uninstall <版本号>`

###### 4. 环境配置

- **自动切换版本**（根据项目 `.node-version` 或 `.nvmrc` 文件）：
  在 Shell 配置文件中添加：
  `eval "$(fnm env --use-on-cd)"`
- **手动加载版本**：
  `fnm env`（需结合 `eval` 命令使用）

###### 5. 其他工具命令

- **查看当前版本**：
  `fnm current`
- **查看帮助文档**：
  `fnm --help`

###### 6.核心优势

- 跨平台支持，性能优于 nvm。
- **无需手动切换路径**，通过 `fnm use` 或配置文件自动管理。
- 兼容 `.node-version` 和 `.nvmrc`，便于项目迁移。



##### 二、VsCode 配置cmder终端

###### 1.安装并配置cmder

###### 2.在VsCode中进行设置

```json
settings.json中添加以下内容:

 "git.enabled": true,
 "git.path": "D:\\Software\\cmder\\vendor\\git-for-windows\\cmd\\git.exe",
 "terminal.integrated.profiles.windows": {
        "Cmder": {
            "path": "D:\\Software\\cmder\\vendor\\git-for-windows\\bin\\bash.exe",
            "args": []
        }
  },
 "terminal.integrated.defaultProfile.windows": "Cmder",
```

**删除旧设置**

```json
"terminal.integrated.shell.windows": "F:\\Program files\\Git\\bin\\bash.exe"
```

###### 3.保存设置，并重新启动VSC查看终端是否设置成功

##### 三、操作文件的查看基本命令

- **中断当前命令：**

  `ctrl + C`

- **查看当前目录的绝对路径：**

  `pwd`

- **查看当前目录内容：**

  `ls`

- **查看指定目录内容:**

  `cat路径`

  `head路径`

  `tail路径`

  `less路径`

##### 四、基本的文件操作命令

- **创建文本** 

  `touch 1.txt `

  `echo hi > 1.txt`

  `echo hihi >> 1.txt`

  `echo -e "1\n2" > 1.txt`

- **创建目录**

  `mkdir a`

  `mkdir -p a/b/c`

- **创建多文本**

  `touch 1.txt 2.txt`

- **创建多目录**

  `mkdir a b`

- **复制文件**

  `cp 1.txt 2.txt`

- **复制目录**

  `cp -r a b`

- **删除文件**

  `rm 1.txt`

- **删除目录**

  `rm -r a`

  `rm -rf a`

- **用VsCode打开文件**

  `code index.html`

- **用VsCode打开文件夹**

  `code .`

- **注意**

  系统文件绝对不能删，创建用户目录，只能在此目录操作

- **前一条命令成功执行后，执行另一条**

  `rm 1.txt && echo 删除成功 && touch 2.txt` 

- **不论前一条命令是否成功执行，仍执行另一条**

  `rm 1.txt ; echo 执行`

- 

##### 五、Git本地仓库操作

```bash
//Git的基本设置
$ git config --global user.name JJ 
$ git config --global user.email JJ@outlook.com		//[key-value]
$ git config --global push.default simple
$ git config --global core.quotepath false
$ git config --global core.editor "code --wait"
$ git config --global core.autocrlf input

$ git config --global --list //查看是否成功执行
//保证在cmder输入code可以直接打开VsCode
//如不执行，需重新安装VsCode并配置PATH
//"PATH": D:\Microsoft VS Code\bin

//"Git功能"
//1.版本控制

$ git init 
//在本项目的文件夹路径下执行此操作
//作用:创建.git目录(代码仓库)，容纳代码快照

$ git add
//向仓库添加需要变动的文件，绝对/相对路径都可以 ./*
// git add . 表示添加当前目录下的所有文件，
//已添加后，Vscoed文件后会出现A,表示已添加成功，未提交显示U

.gitignore
//描述无需提交文件，可在文件目录下设置.gitignore文件，并将无需提交文件名称加入.gitignore文件内
//常见的无需提交的文件node_modules\.DS_Store\.idea\.vscode

$ git status
//查看已提交文件状态

$ git log
//查看git commit -m "引号内容"
$ git reflog
//不止查看回滚版本历史,查看所有提交的版本信息

$ git commit
//正式提交待添加的文件,并说明提交的理由
// git commit -m "版本一"[注意引号]
$ git commit -v
//可以详细知晓所提交文件的具体改动情况并添加详细说明

$ git reset --hard XXXXXX
//功能：进行版本切换
//XXXXXX提交号的前六位
//确保所有代码已commit，否则未commit过的代码会消失

$ git branch x
//建立一个项目分支
$ git checkout x
//进入x分支，对分支项目进行相关操作
//切换分支不影响当前未提交的文件

$ git merge
//合并冲突:鼠标选中每一行,删改完之后保存
//git add index.html ; git commit -v
```

##### 六、Git远程仓库操作

```bash
1.创建ssh key
//cmder操作
$ cd Desktop
$ ssh-keygen -t ed25519 -C "your_email@example.com" [new]
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com" [old] 
//三次回车
$ cd c/Users/Guo/.ssh
$ ls
id_ed25519  id_ed25519.pub
$ cat ~/.ssh/id_ed25519.pub
ssh-ed25519 [公钥]
$ ssh -T git@github.com [测试]
Hi JoshJoe-a! You've successfully authenticated, but GitHub does not provide shell access.

2.本地仓库代码上传
$ git remote add origin git@github.com:JoshJoe-a/[git-demo-2].git
$ git branch -M main
$ git push -u origin main/x

//代码上传至其他分支
$ git push origin x:x
or
$ git checkout x
$ git push -u origin x

3.远程仓库代码下载至本地
$ git clone git@[目标路径/git@github.com:JoshJoe-a/git-demo-1.git]  [clone所有分支]

//若不同机器，需要上传新的ssh key
//cd目标路径
$ git add / git commit / [git pull] / git push 
//如何下载某个分支
//先下载整个仓库，在git checkout x 

4.git命令简化
$ touch ~/.bashrc
$ echo 'alias ga = "git add"' ~/.bashrc
$ echo 'alias gc = "git commit -v"' ~/.bashrc
$ echo 'alias gl = "git pull"' ~/.bashrc
$ echo 'alias gp= "git push"' ~/.bashrc
$ echo 'alias gco = "git checkout"' ~/.bashrc
$ echo 'alias gst = "git status -sb"' ~/.bashrc
$ source ~/.bashrc
```

