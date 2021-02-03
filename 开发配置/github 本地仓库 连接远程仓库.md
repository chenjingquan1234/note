### github 本地仓库 连接远程仓库

#### 建立本地电脑与github ssh连接

打开Git目录下的Git Bash，输入**ssh-keygen**



![img](https://images0.cnblogs.com/blog/385229/201410/301339498002198.png)

一直回车，这里会提示要不要密码，最好不要输入，不然后面每次都要输入

然后会在C:\Users\Administrator下的ssh文件夹生成私钥和公钥

id_rsa和id_rsa.pub。id_rsa是私钥文件，id_rsa.pub是公钥文件

把公钥复制到github上的settings设置中的ssh



![image-20201028151148448](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201028151148448.png)



这样就完成ssh链接

#### 本地仓库与远程仓库关联

现在github上创建新的仓库

![image-20201028151434944](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201028151434944.png)

然后在本地项目 git init 初始化本地项目

```shell
git init
```

然后

```she
git commit -m "xxxx" //第一次提交信息
git branch -M main	//不知道什么用
git remote add origin https://github.com/xxxxx.git   //关联远程仓库
git push -u origin main   //push到远程仓库，第一次要加-u
```



#### 注意事项：

我这里git push -u origin main  的时候报错了

```shel
error: src refspec main does not match any
error: failed to push some refs to 'https://github.com/chenjingquan1234/feiyanjiaoyanduan3.0.git'
```



原因好像是Readme.md文件

然后使用命令

```shel
git pull --rebase origin master
```

拉取更新一次代码，然后在push就成功了