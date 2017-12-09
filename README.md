> Fork 于 [shadowsocks-heroku](https://github.com/mrluanma/shadowsocks-heroku) 项目

# shadowsocks-heroku
[Heroku](https://www.heroku.com/) 是一个支持多种编程语言的云平台即服务，shadowsocks-heroku 则是可部署在 Heroku 平台的ss服务。
和 [shadowsocks](https://github.com/clowwindy/shadowsocks) 不同的是 shadowsocks-heroku 使用的 WebSocket 代替原本的 sockets。

跟着下面的步骤，预计 **十分钟后**，你就可以 Google 了👻。

### 如果遇到问题
请下面列表中寻找解决办法，新问题欢迎[创建issue](https://github.com/521xueweihan/shadowsocks-heroku/issues/new)进行讨论。
- [Error: Cannot find module './merge_sort'](https://github.com/521xueweihan/shadowsocks-heroku/issues/1)

### 一、准备
#### 1.注册 Heroku 帐号
Heroku 提供免费账号，具体限制如下：
- Run apps for free using your monthly pool of free dyno hours
- Unverified accounts: receive a pool of 550 free dyno hours
- Verified accounts: receive an additional 450 free dyno hours
- Dyno hours can be shared across any of your free apps
- 1 web dyno/1 worker dyno/1 one-off dyno maximum per app
- 512 MB RAM per dyno
- Free apps sleep automatically after 30 mins of inactivity to conserve your dyno hours
- Free apps wake automatically when a web request is received
- Access to the Heroku Dashboard and Heroku CLI for app management
- Custom domains for every free app (with verified account)
- Up to 5 free apps (unverified) or 100 (verified)

用作 VPS 是够了，注册地址：https://signup.heroku.com/

#### 2.Fork本项目
1. Fork 本项目到个人账号下
![](https://github.com/521xueweihan/shadowsocks-heroku/blob/master/img/4-min.png)

2. Clone 本项目：`git clone https://github.com/521xueweihan/shadowsocks-heroku.git`

### 二、部署
heroku 在创建项目的时候可以，通过关联 GitHub 账号，直接部署 GitHub 账号下的项目。具体步骤如下：

1. 登陆 Heroku 帐号，后进入 Dashboard ——> Create New App ——> 输入 App Name
2. 完成上一步后，会跳转到 Deploy 页面，找到 Deployment method 选择 GitHub 关联上自己的 GitHub 帐号。
3. 关联上 shadowsocks-heroku 项目，如下图所示：
    ![](https://github.com/521xueweihan/shadowsocks-heroku/blob/master/img/1-min.png)
4. 点击 Deploy Branch，部署成功如下图：
    ![](https://github.com/521xueweihan/shadowsocks-heroku/blob/master/img/2-min.png)

### 三、设置加密算法和密码
Setting 页面 ——> Reveal Config Vars，设置参数如下图：
![](https://github.com/521xueweihan/shadowsocks-heroku/blob/master/img/3-min.png)

**支持的加密算法类型如下：**  
- rc4
- rc4-md5
- table
- bf-cfb
- des-cfb
- rc2-cfb
- idea-cfb
- seed-cfb
- cast5-cfb
- aes-128-cfb
- aes-192-cfb
- aes-256-cfb
- camellia-256-cfb
- camellia-192-cfb
- camellia-128-cfb

### 四、启动本地 client：
1. **进到本项目目录**，执行`npm install` 命令，安装依赖的库（如没有 npm ，请自行安装，[npm安装依赖慢](http://www.cnblogs.com/xueweihan/p/5491730.html)）
2. 启动本地 client，`node local.js -s 你的app名称.herokuapp.com -l 1080 -m 设置的加密算法 -k 设置的密码 -r 80`

### 五、最后
1. 下载：Chrome 浏览器[SwitchyOmega](https://github.com/FelisCatus/SwitchyOmega/releases/download/v2.3.21/SwitchyOmega.crx)，如果下载地址失效，可以在本项目下的 download 下找到 SwitchyOmega.crx
2. 安装：打开浏览器的扩展程序页面 chrome://extensions 。把SwitchyOmega.crx文件拖放到浏览器扩展程序页面安装。
3. 配置：SwitchyOmega：`代理协议：SOCKS5 代理服务器：127.0.0.1 代理端口：1080`，如下图：
![](https://github.com/521xueweihan/shadowsocks-heroku/blob/master/img/5-min.png)
4. 选择代理  
![](https://github.com/521xueweihan/shadowsocks-heroku/blob/master/img/6-min.png)




# shadowsocks-over-websocket
基于 [shadowsocks](https://zh.wikipedia.org/zh-cn/Shadowsocks) 协议的翻墙工具 , 可部署在 [Heroku](https://www.heroku.com/) 平台上 , 实现免费科学上网


## 如何部署在 Heroku 平台上

### 1.准备工作
* [Heroku](https://signup.heroku.com/) 注册
* [GitHub](https://github.com/join?source=header-home) 注册

### 2.Fork [本项目](https://github.com/VincentChanX/shadowsocks-over-websocket) 到个人账号下
![1](./imgs/1.jpg)
进入 <https://github.com/VincentChanX/shadowsocks-over-websocket> 页面  ==>  Fork

---

### 3.创建 [Heroku](https://dashboard.heroku.com/new?org=personal-apps) 应用
![2](./imgs/2.png)
登陆 Heroku 帐号，进入 [Dashboard](https://dashboard.heroku.com/apps) 页面  ==> Create New App ==> 输入 App Name  ==>  Create App

---

### 4.Heroku 帐号与 Github 帐号关联
![3](./imgs/3.jpg)
进入 Deploy 页面 ==> 选择 Deployment Method 为 Github ==> Connect to GitHub

---

### 5.选择要关联的Github项目
![4](./imgs/4.jpg)
选择GitHub帐号  ==> 查找shadowsocks-over-websocket ==> Connect

---

### 6.部署 master 分支

![5](./imgs/5.jpg)

---

### 7.配置环境变量
![6](./imgs/6.png)
Setting 页面 ==> Reveal Config Vars

需要配置 METHOD(加密方法)，PASSWORD(密码，推荐使用`aes-256-cfb`)，SERVER_ADDRESS(`0.0.0.0`) 三个环境变量，支持以下加密方法:

* rc4
* rc4-md5
* table
* bf-cfb
* des-cfb
* rc2-cfb
* idea-cfb
* seed-cfb
* cast5-cfb
* aes-128-cfb
* aes-192-cfb
* aes-256-cfb
* camellia-256-cfb
* camellia-192-cfb
* camellia-128-cfb

---

## 启动客户端：

### 命令行启动:
1. 安装 [nodejs](https://nodejs.org/en/download/) 和 [git](https://git-scm.com/downloads)
2. 执行 `git clone https://github.com/VincentChanX/shadowsocks-over-websocket.git` 命令
1. **进到本项目目录**，执行`npm install` 命令
2. 执行 `node local.js -s app名称.herokuapp.com -l 1080 -m 设置的加密算法 -k 设置的密码 -p 80` 命令，启动成功


## Chrome 浏览器配置
1. 下载 [Chrome](http://www.google.cn/chrome/browser/desktop/index.html) 浏览器插件 [SwitchyOmega](https://github.com/VincentChanX/shadowsocks-over-websocket/raw/master/extensions/SwitchyOmega.crx)

2. 安装 SwitchyOmega 插件：打开浏览器的扩展程序页面 [chrome://extensions](chrome://extensions)，把SwitchyOmega.crx文件拖放到浏览器扩展程序页面安装

3. 新建情景模式 `local-proxy`，配置 SwitchyOmega ：`代理协议：SOCKS5 代理服务器：127.0.0.1 代理端口：1080`，如下图：
![7](./imgs/7.png)

4. 配置 `auto switch` 情景模式，添加规则列表网址: <https://raw.githubusercontent.com/gfwlist/gfwlist/master/gfwlist.txt> 并更新情景模式，规则列表规则处的情景模式选中为上一步创建的 `local-proxy` ，配置如下图:
![8](./imgs/8.png)


5. 选中 `auto switch` 情景模式:
![9](./imgs/9.png)

6. 现在你就可以科学上网了
