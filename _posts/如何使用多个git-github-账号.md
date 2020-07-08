---
title: 如何使用多个git(github)账号
abbrlink: a9c733cc
categories:
- git
date: 2020-07-08 18:55:46
tags:
- git
---

我在公司开发已经使用了公司的git,配置了时使用的git已经存在了git账号,都要支持ssh
## 实现方案

git对用户信息配置有一下几种等级:   
<!-- more -->

### 1.系统级别的配置
配置文件位于`/etc/gitconfig`中,适用于所有的用户和所有的库,可以使用 `$git config --system` 来指定和修改,存储在Git安装目录下
### 2.用户级别的配置
适用于当前登录的用户,可以使用`$git config --gloabal`来指定和修改,存储在`C:\Documents and Settings\$USER`下
### 3.仓库级别的配置
库级别的配置,适用于某个具体的库,可以使用`$git config`来指定和修改,存储在具体的库隐藏的.git文件夹下

几种级别的配置的优先级3>2>1,默认取优先级高的配置.因此可以对公司的git仓库使用系统或用户级配置,而github则使用仓库级配置,每次克隆github的仓库时设置仓库级别的配置

关于SSH key,原有的git已生成了一对文件,这时就需要再为github生成另一组;

## 为github配置SSH key 

进入`.ssh`目录,执行创建ssh key命令

```
    $ ssh-keygen -t rsa -C 87125944@qq.com
```

![生成密钥文件](https://raw.githubusercontent.com/DiamondsMe/source-base/master/_SOURCE_/images/a3b151b2d6a05eaa5e7b989846425ee255657ada.png "生成密钥文件")

根据提示操作npm install,注意新生成的密钥文件名要区别于原有的文件名,这里执行之后
生成密钥文件`id_rsa_github`和公钥文件`id_rsa_github.pub`

## 在github中添加SSH key

复制公钥文件中的文本,访问github.com Setting -> SSH keys -> New Keys

title随心,将刚才复制的内容填入key中并提交;

## 在.ssh目录添加配置文件config

## 将密钥加入到ssh-agent中

ssh-agent是用于管理密钥,执行以下命令将加入到ssh-agent中

```
    ssh-add ~/.ssh/id_rsa_github
```

## 创建config文本文件
在.ssh目录中创建config文件,为每个账号配置单独的host

```
    # 配置github.com
    # 别名 
    Host github.com      

        # 真实的地址
        HostName github.com   

        # id_rsa路径
        IdentityFile ~\.ssh\id_rsa_github

        # 配置登录时用什么权限认证--可设为publickey,password publickey,keyboard-interactive等
        PreferredAuthentications publickey

        # 用户名
        User DiamondsMe 

    # 配置原有的git地址
    Host xxx.com 
        HostName xxx.com 
        IdentityFile ~\.ssh\id_rsa
        PreferredAuthentications publickey
        User nameA 
```

## 执行测试命令测试是否配置成功（管理员身份运行）

```
    $ ssh -T git@github.com

    ssh -T git@github.com The authenticity of host 'github.com (192.30.253.113)' can't be established.

    RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
    Are you sure you want to continue connecting (yes/no)? yes

    Warning: Permanently added 'github.com,192.30.253.113' (RSA) to the list of known hosts.

    Enter passphrase for key '/Users/bj-10026/.ssh/id_rsa_github':
```

如果 

``` 
    Hi DiamondsMe! You've successfully authenticated, but GitHub does not provide shell access.
```

命令执行结束后会在.ssh中生成unknow_host文件

## 创建本地github仓库,配置用户信息

```
    $ git config user.name DiamondsMe
    $ git config user.email 871259441@qq.com
    $ git config --global credential.helper store
```

未使用ssh-add添加

## 尝试提交 

```
    git add . && git commit -m "ci" && git push origin master
```

成功!

![提交信息](https://raw.githubusercontent.com/DiamondsMe/source-base/master/_SOURCE_/images/7e422b820e41705a2358268fc0dc7ea006b399db.png "提交信息")

[Windows下Git多账号配置，同一电脑多个ssh-key的管理][1]   
[Enter passphrase for key每次都需要输入的解决办法][2]   
[Enter passphrase for key每次都需要输入的解决办法][3]
[git 查看/修改用户名、密码][4]



[1]: https://www.cnblogs.com/popfisher/p/5731232.html "Markdown"
[2]: https://www.jianshu.com/p/3d34cb3f4f0d "Markdown"
[3]: https://blog.csdn.net/superbfly/article/details/75287741 "markdown"
[4]: https://blog.csdn.net/ainuser/article/details/79166463 "Markdown" 

