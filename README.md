# Github反向代理并实现登录

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

1. 首先你要有个Github反向代理网站，就简单的反向代理，搭建教程[教程](https://blog.csdn.net/u012424449/article/details/103068412)
2. 别忘了把反向代理地址改为https://github.com，还有要绑自定义域名，还有还有要运行测试一下是否反代成功，又还有要login一下，如果出现如图就可以继续下一步
   ![](https://cloud.shuia.tk/Qexo/2022/8/808a99dafbc186ee45845028e3a9e644.png)
3. 接着在你的浏览器里安装插件Modify Headers或类似修改请求头插件
4. 添加两个Request headers


| Origin             | referer      |
| ------------------ | ------------ |
| https://github.com | 你的镜像域名 |

**提示:referer不一定有用，可能会导致动态跳转到Github静态却不受影响，与你的反向代理服务器有关，自行想办法解决**

5. 如果上一步看不到请[参考](https://blog.csdn.net/weixin_44632787/article/details/118276345)
6. 然后刷新页面，就可以登录了
7. 针对特殊情况:如果登录完没有回到镜像而是去了github官网，再回到镜像站点就ok了

   ![](https://cloud.shuia.tk/Qexo/2022/8/1a3ef1d31023ce70b6a1a600a98519f3.png)

   ## 如果有任何疑问
8. 欢迎提交issue评论
9. ### 参考链接
10. [https://zhuanlan.zhihu.com/p/476390779](https://zhuanlan.zhihu.com/p/476390779)
11. 有服务器的可以参考上面的链接来进行自动化部署
12. 此页面等待更新，还未彻底完成,敬请期待
