# doufu-regram

Quantumult X 重写：把 `https://t.me/...` 外链接 307 跳转到 `regram://` 深链接，强制用 Regram 打开。

目标客户端：[Regram](https://github.com/RegramDev/Regram-ios)（Telegram iOS 分叉，专属 scheme 为 `regram`，另注册 `rg`）。

参考 Surge 模块：[Redirect2Ng by ddgksf2013](https://ddgksf2013.top/module/Redirect2Ng.sgmodule)（原版只有一条 `tg://resolve?domain=$1` 规则，频道帖子、私密邀请、Bot start 参数都会跳错；本仓库拆成 19 条有序规则分别处理）。

## 文件

- `Redirect2Regram_QX.conf` — Quantumult X 原生重写，无需解析器

## 用法

远程重写，在配置 `[rewrite_remote]` 下添加：

```text
https://raw.githubusercontent.com/James-bot2/doufu-regram/main/Redirect2Regram_QX.conf, tag=Redirect2Regram, update-interval=86400, opt-parser=false, enabled=true
```

本地重写：把文件里的 `hostname = t.me, *.t.me` 合并进配置 `[mitm]`，把所有 `url 307` 规则行粘贴到 `[rewrite_local]` 下。

前提：Quantumult X 已开启重写与 MitM，并已安装信任证书；手机已安装 Regram。

本仓库公开，因为 Quantumult X 远程重写需要免登录拉取；文件内无个人数据。
