## node服务部署

先下载xshell 6 ，xftp6

然后连接到服务器，记得要有管理员权限

然后去node官网找对应的node的https下载地址

通过命令 wget 下载这个压缩包

```shell
  wget https://nodejs.org/dist/v12.13.0/node-v12.13.0-linux-x64.tar.xz  
```

// 中间做了通过yum（一个安装依赖包）下载了xz

解压 这个包到目录下 

```shel
 tar xvf node-v12.13.0-linux-x64.tar.xz
```

创建软连接（添加环境变量），使node，npm全局有效

```she
 //注意，下面的空格不是写错了，是需要有空格的
 ln -s /root/node-v12.13.0-linux-x64/bin/node /usr/local/bin/   //目录下的文件
 ln -s /root/node-v12.13.0-linux-x64/bin/npm /usr/local/bin/
```

node-v成功表示安装成功

把项目通过xftp6上传到服务器，

```shel
npm i
npm run build
npm start
```

成功运行后关闭服务,全局下载pm2

```shell
npm install pm2 -g 
```

也要配置全局变量

```shell
ln -s /root/node-v12.13.0-linux-x64/bin/node /usr/local/bin/
```

pm2启动项目

```shell
 pm2 start ./node_modules/nuxt/bin/nuxt.js
```









