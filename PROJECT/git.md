

[toc]

**背景:**

如果你用git clone git@gitlab.xxxx.xxxx/xx.git, shell 报了Permission Denied，很大可能性是由于你没有把自己的ssh(public key)放入到 GitLab/GitHub 里面

**解决办法:**

1. 检查你的本地SSH key 是否存在

```text
ls ~/.ssh/
```

if

生成了， 请把对应的rsa.pub里面的公有key放入gitlab/github里面

else

转步骤2

\2. 生成 ssh key

```text
ssh-keygen -t rsa -b 2048 -C "你自己的邮箱地址"
```

Generating public/private rsa key pair.

Enter file in which to save the key (/c/Users/***/.ssh/id_rsa)

表示你自己的当前登录用户名，不做修改直接回车，会将生成的rsa文件保存为默认名称

再次回车提示：

Enter passphrase (empty for no passphrase):

Enter same passphrase again:

提示设置提交/l拉取代码到Github时需要的密码及确认密码；

设置密码后再次回车提示Your identification has been saved in.... 即表示ssh key生成成功

\3. **添加sshkey至ssh-agent**

```text
    eval "$(ssh-agent -s)"
```



```text
 ssh-add ~/.ssh/id_rsa
```

注意： 如果报Could not open a connection to your authentication agent， 直接把当前git bash窗口关闭了，然后用管理员运行



\4. **添加ssh key至guthub/gitlab**

登入自己的gitlab/github, 点击用户的settings, 然后点击ssh keys, 输入rsa.pub里面存的内容



最后重新运行git clone, 就不报错了



https://zhuanlan.zhihu.com/p/90062634



bilibili

https://www.bilibili.com/video/BV1fh411d7zi?spm_id_from=333.337.search-card.all.click&vd_source=792ad57de3d46edd7c32611a5f65c19e



https://www.jianshu.com/p/2da702603db0



## sourceTree

https://blog.csdn.net/chang_ge/article/details/80796266

