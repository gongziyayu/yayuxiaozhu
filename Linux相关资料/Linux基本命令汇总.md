##Linux基本命令汇总

######vi编辑器基本用法
- <a href="http://linux.chinaunix.net/doc/office/2005-01-24/898.shtml">vi编辑器基本用法</href>
- <a href="http://linux.vbird.org/linux_basic/0310vi.php">图文详解</href>

######查看系统版本命令

```
cat /etc/issue
```
######添加用户相关（需要root登录执行）
```
useradd -m git     		  #用户名
passwd git     			#设置密码，回车后会让输入密码
chmod 740 /etc/sudoers     #将新建的用户添加sudo权限
vi /etc/sudoers            #打开，添加以下内容
<git   ALL=(ALL)  ALL>     #git表示新用户
```