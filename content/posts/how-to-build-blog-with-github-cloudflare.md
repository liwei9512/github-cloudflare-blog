---
title: "如何使用 GitHub + Cloudflare Pages 搭建完全免费的个人博客"
date: 2026-03-10T10:30:00+08:00
draft: false
tags: ["博客搭建", "GitHub", "Cloudflare", "免费工具"]
categories: ["技术文章"]
---

## 为什么选择这个方案？
这是当前个人博客搭建的「天花板级免费方案」，完美匹配 **免费、安全、隐私优先、高可靠** 的需求：
1. ✅ 完全0成本，无任何隐性消费
2. ✅ 隐私100%可控：所有原始内容存在你自己的GitHub私有仓库，任何第三方都无法获取你的草稿、未发布内容
3. ✅ 全球访问速度快：Cloudflare全球300+节点CDN加速，纯静态页面加载仅需几百毫秒
4. ✅ 企业级安全：免费HTTPS、DDoS防护、防入侵，比绝大多数自建站更安全
5. ✅ 无限流量、无限存储空间，无广告打扰
6. ✅ 高度自定义：可以任意更换主题、添加功能，不受平台限制
7. ✅ 内容完全可迁移：所有源文件都在你手里，随时可以迁到其他平台

---

## 前置准备
你只需要两个免费账号：
1. GitHub账号（你Chrome上已经登录了，直接用就行）
2. Cloudflare账号（https://dash.cloudflare.com/sign-up 注册，完全免费）

---

## 步骤1：创建GitHub私有仓库
1. 打开GitHub：https://github.com/new
2. 填写仓库信息：
   - 仓库名：比如 `my-blog`（随便取，英文即可）
   - 仓库类型选择 **Private**（私有，避免你的原始内容、草稿被公开）
   - 勾选 `Add a README file`
   - 点击 `Create repository` 创建完成

---

## 步骤2：上传博客文件到GitHub
我已经帮你生成了完整的博客项目文件，存在你本地的 `/Users/liwei.ok/.openclaw/workspace/github-cloudflare-blog/` 目录下，直接上传到刚才创建的GitHub仓库即可：
1. 打开刚才创建的GitHub仓库页面，点击 `Add file` → `Upload files`
2. 把本地 `github-cloudflare-blog` 目录下的所有文件全部拖到上传框里
3. 点击 `Commit changes` 完成上传

---

## 步骤3：绑定Cloudflare Pages自动部署
1. 打开Cloudflare控制台：https://dash.cloudflare.com/
2. 左侧菜单找到 `Pages` → 点击 `Create project` → 选择 `Connect to Git`
3. 授权Cloudflare访问你刚才创建的GitHub私有仓库
4. 配置部署参数：
   - 项目名称：随便取，比如 `my-blog`，这个就是你的免费二级域名前缀，最终访问地址是 `https://项目名.pages.dev`
   - 生产分支：`main`（GitHub默认分支）
   - 构建命令：`hugo`
   - 构建输出目录：`public`
5. 点击 `Save and Deploy`，等待1分钟左右，部署就完成了！
6. 部署成功后，Cloudflare会给你一个免费的访问地址，打开就能看到你的博客了。

---

## 后续怎么发布新文章？
超级简单，两步搞定：
1. 本地写好Markdown格式的文章，放到 `content/posts/` 目录下
2. 上传到GitHub仓库，Cloudflare会自动编译部署，1分钟后就能在博客上看到新文章。

---

## 可选优化
1. **绑定自定义域名**：Cloudflare Pages支持免费绑定你自己的域名，自动签发SSL证书，全程免费
2. **添加评论功能**：推荐用Giscus（基于GitHub Discussions），支持匿名评论，完全免费，不需要额外服务器
3. **更换主题**：Hugo有上千款免费开源主题，下载后放到themes目录，修改配置文件即可切换
4. **添加全文搜索**：很多主题自带搜索功能，开启即可，不需要额外服务

---

## 避坑提醒
1. 仓库一定要设为私有，否则你的未发布草稿、源文件会被所有人看到
2. 原始Markdown文件建议本地再备份一份，双重保险
3. 不要在博客里泄露个人真实身份、联系方式等敏感信息
