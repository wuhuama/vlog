

- 由于其他项目占用了8080端口,所以,安装live-server 后, 

执行live-server 报错 Error: listen EACCES 0.0.0.0:8080

解决办法:
1. 释放端口
2. 修改默认端口

我才用的是方法2 修改默认端口,找到live-server 的配置文件 index.js,

D:\soft\nodejs\node_global\node_modules\live-server 下的index.js: var port = options.port !== undefined ? options.port : 7999;

然后再次运行: live-server

Serving "F:\project\vuedemo" at http://127.0.0.1:7999






- (我的版本是2.9.3)使用vue-cli 创建新的项目时,总是下载chromedriver失败,所以可以在给npm和yarn设置chromedriver源:

设置`npm config set chromedriver_cdnurl=http://cdn.npm.taobao.org/dist/chromedriver`

设置`yarn config set "chromedriver_cdnurl" "https://npm.taobao.org/mirrors/chromedriver"`

然后再执行 vue init webpack project-name 就OK了