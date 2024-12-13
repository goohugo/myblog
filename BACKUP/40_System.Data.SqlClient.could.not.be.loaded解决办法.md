# [System.Data.SqlClient could not be loaded解决办法](https://github.com/goohugo/myblog/issues/40)

## 问题现象
```
The Entity Framework provider type 'System.Data.Entity.SqlServer.SqlProviderServices, 
EntityFramework.SqlServer' registered in the application config file for the ADO.NET provider with invariant name
 'System.Data.SqlClient' could not be loaded. Make sure that the assembly-qualified name is used and that the 
assembly is available to the running application.
```

这是一个误导人的错误信息，实际是因为找不到 EntityFramework.SqlServer.dll 文件。
问题背景是web项目所引用的项目中安装了EF的nuget包，而web项目本身没有安装。于是build后，web项目的bin文件夹中只有EntityFramework.dll，却没有EntityFramework.SqlServer.dll。


## 解决方案
web项目也安装Entity Framework的nuget包。

> 把所引用的项目中安装了EF的nuget包的bin目录下的EntityFramework.SqlServer.dll 文件复制到Web项目中的bin目录下
