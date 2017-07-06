######vps搭建hexo信息

****
- <a href="http://www.cnblogs.com/lianer/p/5836194.html">hexo搭建博客的参考链接</a>
****

1. debian系统安装 nginx   (<a href="http://www.linuxidc.com/Linux/2017-03/141260.htm">点击进入原参考地址</a>)

 - 编辑 /etc/apt/sources.list ，添加以下两行。（Debian版本代号分别为5.0的 lenny，6.0的 squeeze ，7.0的 wheezy 和8.0的 jessie，至于还没发布的9.0则为 stretch，你只需要根据你使用的版本更换对应的版本代号即可）
```
deb http://nginx.org/packages/debian/ 版本代号 nginx
deb-src http://nginx.org/packages/debian/ 版本代号 nginx
```
 - 更新并导入升级Key
```
wget http://nginx.org/keys/nginx_signing.key && apt-key add nginx_signing.key && apt-get update && apt-get install nginx
```

2. debian系统安装node js (<a href="http://blog.csdn.net/ysynhtt/article/details/44594919">点击进入原参考地址</a>)【以下脚本非root用户前面加上sodu】
  - 下载源码(去官网找到能用的最新的替掉node-v0.12.1.tar.gz)
```
wget http://nodejs.org/dist/node-v0.12.1.tar.gz
```
 - 安装g++ （如果已经安装，可跳过）
```
 apt-get install g++
  apt-get install pkg-config  (必须，如果不执行有可能编译不通过)
```
 - 解压，安装
```
tar zxvf node-v0.4.9.tar.gz
  cd node-v0.4.9
  ./configure
  make 
  make install
```
 - 检验版本
```
node -v
```

3. git安装
```
apt-get install git
```

4. hexo模块安装
```
cd ~/hexo
npm install hexo-cli -g
npm install
//进入文件夹
hexo init
```
//hexo初始化之后，使用的默认主题；可以使用 git clone xxx  theme/xx  将需要的主题下载到themes文件夹
//然后切换到目标文件夹 ，可以使用git命令【注意一定要打开clone的目标文件夹
//对于写得文章，同第二步
```
git clone  https://github.com/gongziyayu/gumoxiang.git  theme/yilia
```

5. nginx的配置
  - 新建个配置文件
```
cd /etc/nginx/conf.d/
vi hexo.conf
```
  - 配置内容
```
server {
    listen          80;
    server_name     imlianer.com www.imlianer.com;  # 你的域名
    location /root{
        root         hexo;
        index        index.html;
    }
}
```
 - 重新加载或启动
```
nginx -s reload
```
****
到此处，就可以输入自己的域名进行访问了，前提是你将域名解析到主机中，下一个记录自动化部署的问题。
****



