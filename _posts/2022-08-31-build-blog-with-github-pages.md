---
tags: 免费博客 免费域名
---

## 在Github Pages上搭建免费的blog系统

前言

**让我们开始吧**

### 搭建blog系统
#### 创建系统
1. 创建Github账号
    
    [注册并创建Github账号](https://github.com/signup)

2. 使用模板创建自己的第一个仓库，也就是blog

    Github Pages基于kelyll来实现blog系统，我们使用现有的模板 [https://github.com/chadbaldwin/simple-blog-bootstrap/generate](https://github.com/chadbaldwin/simple-blog-bootstrap/generate)

3. 命名并创建blog仓库

    * 输入仓库名称
      输入自己的github账号名称 + ".github.io"， 比如你的github账号为 “zhangerga” 就输入
      ```
      zhangerga.github.io
      ```
      **这里非常重要，否则无法访问**
      
 4. 在根目录创建CNAME文件

#### 自定义布局和风格

#### 撰写及发布新文章

### 申请免费域名
现在可以申请免费域名的服务商不多， [freenom](https://www.freenom.com/)是我能找到的比较靠谱的一家， 可一次性免费申请12个月有效期，到期前两周内可以申请新的有效期。根据用户协议，申请的免费域名需要指向面向公众的网站，以下几种情况域名可能会被回收：

* 域名没有指向有实际内容的网站
* 域名指向的网站只有注册用户可以访问

### 通过Cloudflare实现域名访问
在cloudflare中添加域名

在域名服务商的控制面板添加cloudflare的DNS作为域名解析服务器， 如果是在[freenon](https://www.freenom.com/)申请的免费域名，可以到域名下更改DNS Server


域名添加成功后， 开启SSL/TLS访问， 选择加密模式为Full 完全
Edge Certificates 边缘证书 页面选择 Always Use HTTPS 始终使用HTTPS， 这样当在浏览器输入http时会自动重定向到https

添加规则， 在规则下面创建 页面规则， 
URL填写域名， 如果不想带www访问，直接填写域名即可，比如 “zhangerga.ml”， 设置下选择 “Always Use HTTPS“ 总是使用HTTPS


