## gorpxoy-heroku

### Heroku 是一个支持多种编程语言的云平台即服务，gorpxoy-heroku 则是可部署在 Heroku 平台的 gorpxoy 服务。gorpxoy-heroku 使用的 WebSocket 代替原本的 sockets 作为底层传输。

#### 下面的部署方法，前提是你已经拥有一个heroku账号。

1.注册 Heroku 帐号

Heroku 提供免费账号，部分介绍如下：

512 MB RAM per dyno

Free apps sleep automatically after 30 mins of inactivity to conserve your dyno hours

Free apps wake automatically when a web request is received

https://devcenter.heroku.com/articles/limits

https://devcenter.heroku.com/articles/free-dyno-hours#usage

注册地址：https://signup.heroku.com/ （注册和部署过程可能需要梯子）


## 部署方法一（简单）

本方法为快速部署。

一、在heroku上的部署

1、登陆https://dashboard.heroku.com/login

2、登陆好后，点击

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy?template=https://github.com/snail007/goproxy-heroku)

3、执行以下三个步骤，见下图：

（1）输入App name.例如`test1-goproxy`

（2）Choose a region:选择一个.例如United States

（3）点击：Deploy app

<img src="/doc/1.png" width="500px" height="auto">

4、执行完成以后，这是就完成了部署。

<img src="/doc/2.png" width="500px" height="auto">

二、在客户端上执行

独立goproxy客户端：

`proxy.exe http -t tcp -p :6600 -T wss -P test1-goproxy.herokuapp.com:443 --parent-ws-password pass -q 8.8.8.8:53 --timeout 30000`

在浏览器上设置代理：127.0.0.1:6600   http

安卓客户端：

安卓 [goproxy-ss-plugin](https://github.com/snail007/goproxy-ss-plugin-android) 插件配置可以写：

```text
主机：test1-goproxy.herokuapp.com

端口：443

加密方法：aes-256-cfb

密码：123

插件参数：
```

`-S http -j 123 -h aes-256-cfb -T wss -P test1-goproxy.herokuapp.com:443 --parent-ws-password pass --timeout 30000`

注意：本次部署中需要调整的就是`test1-goproxy`改为你自己的名称。

## 部署方法二

该方法相对方法一步骤多一些，但是可以自己设置加密密码，修改启动参数。

本方法是fork项目后，可以修改相关的参数，再在heroku上部署。

一、在github上fork该项目并修改相关参数

（1）fork项目：https://github.com/snail007/goproxy-heroku

（2）修改配置参数，具体就是修改bootstrap里的内容，点击该文件

<img src="/doc/2.1.png" width="500px" height="auto">

修改第7行内容，详细参考：https://snail007.github.io/goproxy/posts/http_cdn_ws/

二、在heroku上部署

1、登陆https://dashboard.heroku.com/apps

2、选择New -> Create new app

<img src="/doc/2.2.png" width="500px" height="auto">

3、执行以下三个步骤，见下图：

（1）输入App name.例如`test2-goproxy`

（2）Choose a region:选择一个.例如United States

（3）点击：Create app

<img src="/doc/2.3.png" width="500px" height="auto">

选择Deploy->GitHub Connect to github

<img src="/doc/2.4.png" width="500px" height="auto">

4、连接到自己的github，搜索goproxy-heroku项目，点击连接Connect

<img src="/doc/2.5.png" width="500px" height="auto">

5、手动部署Manual deploy -> Deploy Branch， 部署成功。

<img src="/doc/2.6.png" width="500px" height="auto">
<br>
<img src="/doc/2.7.png" width="500px" height="auto">

三、在客户端上执行（默认不修改代码）

独立goproxy客户端：

`proxy.exe http -t tcp -p :6600 -T wss -P test2-goproxy.herokuapp.com:443 --parent-ws-password pass -q 8.8.8.8:53 --timeout 30000`

在浏览器上设置代理：127.0.0.1:6600   http

安卓客户端：

安卓 [goproxy-ss-plugin](https://github.com/snail007/goproxy-ss-plugin-android) 插件配置可以写：

```text
主机：test2-goproxy.herokuapp.com

端口：443

加密方法：aes-256-cfb

密码：123

插件参数：
```
`-S http -j 123 -h aes-256-cfb -T wss -P test2-goproxy.herokuapp.com:443 --parent-ws-password pass --timeout 30000`

注意：本次部署中需要修改test2-goproxy为你自己的名称。
