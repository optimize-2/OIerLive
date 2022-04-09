# OIerLive
某大型线上网络游戏防划水神器（OIer 屏幕分享软件）

# 免责声明
使用本软件即默认您已阅读 [互联网直播服务管理规定](http://www.cac.gov.cn/2016-11/04/c_1119847629.htm)。
本软件仅支持定时上传屏幕截图，不含录音，录屏，打赏互动等功能。
本软件仅供在做题时分享屏幕与做题笔记使用，造成的后果开发者概不负责。

用户群：1025329276

# 搭建教程

需要 **同时搭建** 前端（front）和后端（back），服务才能生效。

## 前端搭建教程

1. 配置 nodejs 环境。

2. 把仓库 `clone` 到本地。

3. 安装依赖。
  ```
  cd front
  yarn
  ```

4. 修改 `config.json`。
  ```
  {
      "password": "你的密码（应与后端密码一致）",
      "interval": "更新画面的间隔（单位：ms）",
      "server": "post 方法地址（后文会讲到）"
  }
  ```

## 后端搭建教程

| 后端 | 优点 | 缺点 | 部署教程 |
| :-----------: | :-----------: | :-----------: | :-----------: |
| Tencent SCF | 命令行一键部署，速度快，多文件代码易懂 | 价格贵 | [here](/back/tencentSCF/README.md) |
| Cloudflare Worker | 每天十万次免费调用额度 | 绑定数据库部署复杂，单文件代码不易读 | [here](/back/cloudflareWorker/README.md) |

# 使用教程

前后端都搭建完成后， 在 `front` 目录内执行如下命令：
```
npm run start
```

若看见如下的运行日志，则说明部署成功。
```
Screenshoting...
Syncing data...
Received response!
```

对于腾讯云函数，可以访问 `triggers` 的第二项 `live` 来进入屏幕分享页面，在本例中为 `http://service-65f7tzkx-1305163805.sh.apigw.tencentcs.com/release/live`。

对于 cloudflare worker，可以访问 `Workers` 地址后面加 `/live` 来进入屏幕分享页面，在本例中为 `https://live.op2.workers.dev/live`。

通过修改 `front/live/note.txt` 可以同步做题笔记，支持 markdown 语法。

若要停止屏幕分享，关闭执行过 `npm run start` 的终端即可。

# 更新教程
在命令行中执行如下命令.
```
git pull
```
若更新了前端，直接重启即可。
若更新了后端，使用对应的部署方式即可。
```
# cloudflare
wrangler publish
# tencent
serverless deploy
```

# 绑定域名

腾讯云函数的默认域名太长，若要绑定域名，可以在 [腾讯云函数控制台](https://console.cloud.tencent.com/scf/list) 中操作，也可以解析到云函数。
Cloudflare Worker 可以在 Cloudflare dash 中绑定域名，也可以解析到 `Worker`。
未来也可能实现将屏幕分享域名与 [OIerSpace](https://oier.space) 开通了 Pro Plan 的个人博客绑定。

# 问题反馈

加入用户群 1025329276 或使用 Github Issue 反馈。

# 支持我们

根据相关法律法规，本软件完全免费，若真的想支持我们，可以赞助我们的其他项目：[Extend Luogu](https://afdian.net/@extend-luogu) / [OIer Space](https://afdian.net/@bohan)。
