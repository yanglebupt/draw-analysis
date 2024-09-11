# 如何 Push 代码

将私钥 `draw-analysis` 拷贝到你的电脑上，并添加到 `~/.ssh` 目录下

```shell
mv <PATH OF PRIVATE KEY> ~/.ssh
cd ~/.ssh
chmod 0600 ./draw-analysis
```

如果 `~/.ssh` 目录下不存在 `config` 文件，则新建 `touch config`，然后在 `config` 文件末尾写入

```shell
Host draw-analysis.com
  HostName github.com
  PreferredAuthentications publickey
  IdentityFile /root/.ssh/draw-analysis
```

测试连接 `ssh -T git@draw-analysis.com`，成功后可以正常连接 git 了，在 `.gitignore` 中注意不要上传数据集、保存的模型、暂存文件等

```.gitignore
绘画分类数据集/**
results/**
dataset/**
**/.ipynb_checkpoints
**/.pytest_cache
**/__pycache__
```

配置 git 信息

```shell
cd <project>
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```

开始上传，注意每个人新建一个分支上传，可以以自己的名字命名分支名字 `git checkout -b <your-name>`

```shell
git init
git add .
git commit -m <COMMIT-MESSAGE>
git remote add origin git@draw-analysis.com:yanglebupt/draw-analysis.git
git push origin <your-name>
```
