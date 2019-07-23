## gorpxoy-heroku

### Heroku 是一个支持多种编程语言的云平台即服务，gorpxoy-heroku 则是可部署在 Heroku 平台的 gorpxoy 服务。gorpxoy-heroku 使用的 WebSocket 代替原本的 sockets 作为底层传输。

### 如果遇到问题

请先检查是否遵循步骤（再次阅读一遍教程）

请先自行通过Google/Github寻找答案

如果还没有解决，欢迎通过 issue 提问（贴日志和配置的时候注意隐藏密码&个人ip）

## 准备

为了保证不出错，下面的操作均需要在Linux系统下面执行。而且已经安装了git命令。

### 1. 注册 Heroku 帐号

Heroku 提供免费账号，部分介绍如下：

512 MB RAM per dyno

Free apps sleep automatically after 30 mins of inactivity to conserve your dyno hours

Free apps wake automatically when a web request is received

https://devcenter.heroku.com/articles/limits

https://devcenter.heroku.com/articles/free-dyno-hours#usage

注册地址：https://signup.heroku.com/ （注册和部署过程可能需要梯子）

### 2.安装heroku-cli

官方参考地址：https://devcenter.heroku.com/articles/heroku-cli

### 3.本地登录heroku

当步骤1和2完成之后，你本地应该可以直接执行heroku命令，执行`heroku status`检查是否登录。

### 4.部署goproxy到heroku

一键安装命令：

`curl -L https://raw.githubusercontent.com/snail007/goproxy-heroku/master/deploy.sh | bash`

执行成功之后，会输出一个你的heroku APP的https访问地址，这个地址就是goproxy sps功能连接的地址，ws密码是pass。





