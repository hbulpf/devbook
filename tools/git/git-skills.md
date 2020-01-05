# git push 本地不用输入用户名密码

1. 进入~（用户）目录: `cd ~`
2. 建立文件 .git-credentials: `touch  .git-credentials`

3. 编辑文件 .git-credentials： `vi  .git-credentials`

4. 添加 https://用户名:密码@gitlab.com

5. 执行命令：`git config --global credential.helper store`

6. 查看文件：`more .gitconfig` 可以看到如下信息，设置成功。

    ```
    [push]
        default = simple
    [user]
        name = test
        email = test@gitlab.com
    ```

4，5步骤也可以换成，在 `.git-credentials` 中加上如下内容

```
[user]
    email = test@gitlab.com
    name = test

[credential]
    helper = store
```

# github 网页加载慢问题

windows 进入 `C:\Windows\System32\drivers\etc` 目录， 在 `hosts` 最后加入以下解析内容。

```
# GitHub Start 
# 13.250.177.223	github.com
#解决git clone 速度慢的问题
192.30.253.112 github.com
151.101.185.194 github.global.ssl.fastly.net
#解决浏览器下载master-zip包的问题
192.30.253.120 codeload.github.com
192.30.253.119    gist.github.com
151.101.184.133    assets-cdn.github.com
151.101.184.133    raw.githubusercontent.com
151.101.184.133    gist.githubusercontent.com
151.101.184.133    cloud.githubusercontent.com
151.101.184.133    camo.githubusercontent.com
151.101.184.133    avatars0.githubusercontent.com
151.101.184.133    avatars1.githubusercontent.com
151.101.184.133    avatars2.githubusercontent.com
151.101.184.133    avatars3.githubusercontent.com
151.101.184.133    avatars4.githubusercontent.com
151.101.184.133    avatars5.githubusercontent.com
151.101.184.133    avatars6.githubusercontent.com
151.101.184.133    avatars7.githubusercontent.com
151.101.184.133    avatars8.githubusercontent.com
# GitHub End
```

# 常见的 基于 git 的网站

网站 | 国家 |
--- | --- |
[github](https://github.com) | 美国
[gitlab](https://gitlab.com)  | 美国
[gitee](https://gitee.com/)  | 中国大陆