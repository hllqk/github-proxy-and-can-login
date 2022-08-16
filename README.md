# Github反向代理并实现登录

##### 说明：此教程是基于无服务函数和浏览器插件的实现，如想要一键搭建部署，请参考[https://zhuanlan.zhihu.com/p/476390779](https://zhuanlan.zhihu.com/p/476390779)

![](https://cloud.shuia.tk/Qexo/2022/8/162fc2b7fd4fdc46149377d1e6a6dbab.png)

## 实现功能

* [X]  登录
* [X]  注册
* [X]  创建仓库
* [X]  修改
* [X]  更多

### 总之就是Github，完全的gtihub

**解决了国内总是打不开的问题，国人福音！**

## 开始教程

1. 首先你要有个Github反向代理网站，就简单的反向代理，搭建教程，自己[bing](https://cn.bing.com/search?q=%E5%8F%8D%E5%90%91%E4%BB%A3%E7%90%86Github&qs=n&form=QBRE&sp=-1&pq=%E5%8F%8D%E5%90%91%E4%BB%A3%E7%90%86github&sc=1-10&sk=&cvid=789F3AE646004FCDBD6DA1F7248F16D6&ghsh=0&ghacc=0&ghpl=)注意cf worker搭建的没有用，根本无法登录，建议用serverless搭建如[vercel](https://vercel.com/)或者[netfly](https://www.netlify.com/)
2. 别忘了把反向代理地址改为https://github.com，还有要绑自定义域名，还有还有要运行测试一下是否反代成功，又还有要login一下，如果出现如图就可以继续下一步
   ![](https://cloud.shuia.tk/Qexo/2022/8/808a99dafbc186ee45845028e3a9e644.png)
3. 接着在你的浏览器里安装插件Modify Headers或类似修改请求头插件
4. 添加配置
   **Request headers配置**

   自动添加

   ```json
   [{"version":2,"title":"Profile 1","headers":[{"enabled":true,"name":"Origin","value":"https://github.com"},{"enabled":true,"name":"referer","value":"你的github反向代理域名"}],"urlReplacements":[{"enabled":true,"name":"https://github.com/(.*)","value":"你的github反向代理域名/$1"}],"urlFilters":[{"enabled":true,"urlRegex":".*://你的github反向代理域名/.*"},{"enabled":true,"urlRegex":".*://github.com/.*"}],"shortTitle":"1"}]
   ```

将以上配置导入import不会导入看下文官方文档

##### 手动添加


| Origin             | referer      |
| ------------------ | ------------ |
| https://github.com | 你的镜像域名 |

**Redirect URLs配置**


| https://github.com/(.*) |
| ----------------------- |
| 你的github反向代理域名/$1   |

**URL filters配置**


| .*://你的反向代理域名不加http/.* |
| -------------------------------- |
| .*://github.com/.*               |

##### ***看不懂配置?[点我查看文档](https://docs.modheader.com/using-modheader/introduction)***

5. 浏览器插件问题请[参考](https://blog.csdn.net/weixin_44632787/article/details/118276345)
6. 然后刷新页面，就可以登录了
7. 针对特殊情况:已经解决特殊情况

   ![](https://cloud.shuia.tk/Qexo/2022/8/1a3ef1d31023ce70b6a1a600a98519f3.png)

   ## 如果有任何疑问
8. 欢迎提交issue评论
9. ### 参考链接
10. [https://zhuanlan.zhihu.com/p/476390779](https://zhuanlan.zhihu.com/p/476390779)
11. 有服务器的可以参考上面的链接来进行自动化部署
12. 此内容待定，等待更新
13.[原文](https://hllqk.vercel.app/2022/08/14/githubproxy/)
#### 自言自语

其实可以直接rewrite和重定向在无服务函数实现的，奈何官方文档看不懂，网上也没有类似的教程，所以才采用了浏览器插件实现，反正效果都一样
