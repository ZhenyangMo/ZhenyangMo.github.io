---
title: 如何零成本给博客集成 umami 数据统计分析功能
date: 2022-08-14T21:34:36+08:00
tags: ["hugo", "ladder", "教程", "analytics", "umami"]
series: ["how to create your blog"]
featured: true
---
本篇文章介绍如何零成本给博客或者网站集成 [umami](https://umami.is/) 统计功能。数据库用的是 [supabase](https://app.supabase.com/) 提供的有限额的 [postgres](https://supabase.com/docs/guides/database)，不过免费提供的 500M 对于  [umami](https://umami.is/) 来讲已经足够了。

托管 [umami](https://umami.is/) 服务用的是 [vercel](https://vercel.com/)。得益于现在的云厂商优秀的服务能力，你可以在 10 分钟内集成好 *umami*。可以点击 [数据统计看板](https://umami-ochre-nu.vercel.app/share/o3zAba1V/guangzhengli) 查看最终效果。

<!--more-->

## 创建数据库

数据库用的是 [supabase](https://app.supabase.com/) 提供的有限额的 [postgres](https://supabase.com/docs/guides/database) 数据库，创建一个 supabase 账号，新建一个项目，输入 Datebase password 即可创建数据库服务。

![cN3Zg4](https://cdn.jsdelivr.net/gh/guangzhengli/PicURL@master/uPic/cN3Zg4.png)

创建可能会话费几分钟时间，创建完成后只需要拿到 `DATABASE_URL` 即可。

![image-20220815182141638](https://cdn.jsdelivr.net/gh/guangzhengli/PicURL@master/uPic/image-20220815182141638.png)

## 托管 umami

托管 [umami](https://umami.is/) 服务用的是 [vercel](https://vercel.com/)。创建好数据库实例之后，可以通过 Vercel 一键部署 umami 服务了。访问 [umami 官方文档](https://umami.is/) 的 [Running on Vercel](https://umami.is/docs/running-on-vercel) 模块，有操作说明与一键部署脚本。

首先我们登录 GitHub 账号， `fork` umami (https://github.com/umami-software/umami) 项目。

登录 [vercel](https://vercel.com/) ，创建一个的账号，建议使用 GitHub 账号注册登录，在 `new project` 中选择 `import` 你刚刚 `fork` 的项目。

之后填写环境变量，这里我们需要填写两个环境变量

* DATABASE_URL：在创建数据库中拿到的 DATABASE_URL
* TRACKER_SCRIPT_NAME： 这里默认的 `tracker_script_name` 可能会导致部分  `AdBlock` 拦截请求，损失一部分的访问数据，所以这里我填的是 `hugo-ladder`。

最后在 Build 阶段， `build command`  记得填写 `yarn build && yarn update-db`，这样的话会自动 migrate 数据库的表。无需自己手动导入。

![gePzXI](https://cdn.jsdelivr.net/gh/guangzhengli/PicURL@master/uPic/gePzXI.png)

当然如果你想自己导入的话，也可以直接从这里 https://github.com/umami-software/umami/blob/master/sql/schema.postgresql.sql 获取需要的表。

## 配置 umami

在 vercel 部署完成 umami 后会得到一个 `<deploy-id>.vercel.app` ，我们访问它，默认的账号密码是 **admin** 和 **umami**。

完成基础帐号配置后，点击侧边栏网站 Tab，点击添加网站。填写网站基本信息，可以勾选 `enable share URL`，这样任何人都可以访问这个数据看板。

我们拿到对应的 `data-website-id` 和 `src` ，填入主题配置中的 `params.analytics.umami.website_id` 和  `params.analytics.umami.url` 即可。 

![OZcU7U](https://cdn.jsdelivr.net/gh/guangzhengli/PicURL@master/uPic/OZcU7U.png)

最终，我们可以得到本站数据统计看板的功能🎉🎉🎉

原文链接: https://guangzhengli.com/zh/blog/zh/how-to-integrate-umami-for-free-to-blog-site/
