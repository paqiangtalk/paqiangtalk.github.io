---
layout: post
title: 在Github Pages上免费搭建blog系统  
tags: 免费博客 免费域名
hero_image: /images/bg/website-1920.jpg
---



前段时间折腾升级自用了10年的NAS，硬件升级，存储从raid 1迁移到 snapraid，经历一番曲折也获得了一些经验，于是想写下来做个记录以便日后需要的时候方便查询，同时可以分享给同样需求的朋友们。虽然自己也有几个vps空间， 可以很方便的搭建起blog系统。不过github提供了免费方案， 白嫖也未尝不可， 过程非常简单，你也可以试一下。

**Let's go**

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
	在CNAME文件内添加自己的域名，比如 `zhangerga.com`，用来直接访问blog
	

#### 自定义布局和风格
 修改`_layouts`目录下的html文件改变布局，`post.html`为文章渲染模板  
`css`目录内的css文件可以修改渲染风格

#### 撰写及发布新文章
  然后就可以开启博客之旅了， 所有的文章都在`_posts`目录下， 命名方式以完整的日期格式开始，加上文章标题，后缀为`.md`，比如： `2022-08-31-first-article.md`  
  
  在发布或者修改文章后，需要等待一段时间等github pages后台处理，一般2分钟以内刷新浏览器就可以了。
  
  如果需要图片，可以在根目录创建一个目录用于存放上传的图片，比如`images`,然后在文章中直接引用即可

### 申请免费域名
现在可以申请免费域名的服务商不多， [freenom](https://www.freenom.com/)是我能找到的比较靠谱的一家， 可一次性免费申请12个月有效期，到期前两周内可以申请新的有效期。根据用户协议，申请的免费域名需要指向面向公众的网站，以下几种情况域名可能会被回收：

* 域名没有指向有实际内容的网站
* 域名指向的网站只有注册用户可以访问

 * 检查可用域名
   ![](/images/2022-08-31/freenom-register-domain.png)

     **_这里需要注意：在查询域名是否可用时，应该带上根域名， 否则在选择页面点击“选择”按钮时会显示所选域名不可用_**

     ![](/images/2022-08-31/freenom-checkout.png)
     
   * 完成  
     点击“Checkout （完成）” ，如果没有注册过账号，需要输入email地址完成注册并申请域名

### 通过Cloudflare实现域名访问
* 在cloudflare中添加域名  
  cloudflare会检测域名的DNS记录以及DNS解析服务器
  
  在域名服务商的控制面板添加cloudflare的DNS作为域名解析服务器， 如果是在[freenon](https://www.freenom.com/)申请的免费域名，可以到域名下更改DNS Server为cloudclare提供的域名解析服务器，比如  

  ```
  kayden.ns.cloudflare.com
  tricia.ns.cloudflare.com
  ```
  分别填入DNS 1 和DNS 2即可

* 开启SSL/TLS  
	域名添加成功后， 开启SSL/TLS访问， 选择加密模式为Full 完全  
	![](/images/2022-08-31/cloudflare-ssl.png)
	
	Edge Certificates 边缘证书 页面选择 Always Use HTTPS 始终使用HTTPS， 这样当在浏览器输入http时会自动重定向到https
	![](/images/2022-08-31/cloudflare-always-https.png)

* 添加规则  
	在规则下面创建 页面规则  
	URL填写域名， 如果不想带www访问，直接填写域名即可，比如 “zhangerga.ml”， 设置下选择 “Always Use HTTPS“ 总是使用HTTPS


浏览器中输入https://域名 即可访问自己的blog了👍
