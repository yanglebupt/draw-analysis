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

测试连接 `ssh -T git@draw-analysis.com`，成功后可以正常连接 git 了

```
cd <project>
git init
git add .
git commit -m "first commit"
git branch -b <your-name>
git remote add origin git@draw-analysis.com:yanglebupt/draw-analysis.git
git push origin <your-name>
```