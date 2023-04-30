# [git中的SSL证书问题：无法获取本地颁发者证书错误的解决办法](https://github.com/haoz0x139/myblog/issues/10)

我们在使用git初始化一个项目时，尤其是通过git submodule update --init --remote初始化子模块时，可能会遇到下面这个错误：
fatal: unable to access 'https://myserver.com/gogs/user1/myapp/': SSL certificate problem: unable to get local issuer certificate

这是由于当你通过HTTPS访问Git远程仓库的时候，如果服务器上的SSL证书未经过第三方机构认证，git就会报错。原因是因为未知的没有签署过的证书意味着可能存在很大的风险。解决办法就是通过下面的命令将git中的sslverify关掉：
```
git config --global http.sslverify false
```
上面这行命令的影响范围是系统当前用户，如果要设置为全局所有用户，可以改成这样：
```
git config --system http.sslverify false
```
如果只是想针对当前仓库进行设置，可以在需要修改的仓库目录下执行：
```
git config http.sslverify false
```
如果你的仓库中存在嵌套的git子模块（就是子模块中又引用了子模块），在进行初始化时，仍然有可能遇到self signed certificate in certificate chain的错误，此时可以通过执行下面的命令来解决：
```
npm config set strict-ssl false
```
对于npm而言，除了可以在package.json的scripts属性中自定义脚本外，npm-scripts也内置了一些脚本，用来在特定的时机执行某些特定的任务，具体可以参照npm的官方文档https://docs.npmjs.com/misc/scripts