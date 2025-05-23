---
date: 2025-05-22
category:
  -操作系统
tag:
  - 面试题
---


# 说说你对 linux 用户管理的理解？相关的命令有哪些？

 ![](https://static.vue-js.com/8d8d9d70-0417-11ec-8e64-91fdec0f05a1.png)



## 一、是什么

Linux是一个多用户的系统，允许使用者在系统上通过规划不同类型、不同层级的用户，并公平地分配系统资源与工作环境

而与 `Windows` 系统最大的不同， `Linux` 允许不同的用户同时登录主机，同时使用主机的资源

既然是多用户的系统，那么最常见的问题就是权限，不同的用户对于不同的文件都应该有各自的权限

例如，小 A 希望个人文件不被其他用户读取，而如果不对文件进行权限设置，共享了主机资源的小 B 也可以读取小 A 的个人文件，这是不合理的

这里面涉及到用户与用户组的概念



## 二、用户与用户组

`Linux `以 “用户与用户组” 的概念，建立用户与文件权限之间的联系，保证系统能够充分考虑每个用户的隐私保护，很大程度上保障了 `Linux` 作为多用户系统的可行性

从文件权限的角度出发，“用户与用户组” 引申为三个具体的对象：

- **文件所有者**
- **用户组成员**
- **其他人**

每一个对象对某一个文件的持有权限是不同的



### 文件所有者

当一个用户创建了一个文件，这个用户就是这个文件的文件所有者。文件所有者对文件拥有最高权限，同时排他性地拥有该文件

除非文件所有者开放权限，否则其他人无法对文件执行查看、修改等操作



### 用户组

将 “其他用户” 区分为用户组成员和其他人后，若文件所有者希望对部分用户开放权限，而对其他人继续保持私有，则只需要将这部分用户与文件所有者划入一个用户组

这样，这部分用户就成了与文件所有者同组的用户组成员。用户可以对用户组成员开放文件权限，用户组成员则具备了查看、修改文件的权限，而对其他无关用户保持私有

例如，团队成员之间保持文件资源共享，但对非团队成员保持私有，这就需要将文件所有者与团队成员用户划分为同一个用户组，再对用户组成员开放权限即可



### 其他人

既与文件所有者没有任何联系的其他用户



### 小结

户和用户组的对应关系是：一对一、多对一、一对多或多对多：

- 一对一：某个用户可以是某个组的唯一成员
- 多对一：多个用户可以是某个唯一的组的成员，不归属其它用户组
- 一对多：某个用户可以是多个用户组的成员
- 多对多：多个用户对应多个用户组，并且几个用户可以是归属相同的组



### 拓展

当我们使用`ls -l`的时候，会列出当前目录的文件信息，如下：

```cmd
drwxr-xr-x   3  osmond   osmond    4096  05-16 13:32   nobp
```

- d：文件类型
- rwxr-xr-x：文件权限
- 3 硬链接数或目录包含的文件数
- osmond：文件所有者
- 4096：文件长度
- 05-16 13:32：文件上次修改的事件和日期
- nobp：文件名

下面主要看看文件权限分析，实际上是由9个字符组成，每3个一组：

- 第一组控制文件**所有者**的访问权限
- 第二组控制所有者**所在用户组**的其他成员的访问权限
- 第三组控制**系统其他用户**的访问权限

`-`代表当前没有，`rwx`对应代表的意思如下：

 ![](https://static.vue-js.com/9ac2cf60-0417-11ec-8e64-91fdec0f05a1.png)





### 三、用户操作



用户相关的操作有如下：

### 新增用户

`useradd` 可以用来创建新用户，简要语法为：

```text
useradd [options] [username]
```

例如：

添加一个一般用户

```
# useradd kk //添加用户kk
```

为添加的用户指定相应的用户组

```
# useradd -g root kk //添加用户kk，并指定用户所在的组为root用户组
```

创建一个系统用户

```
# useradd -r kk //创建一个系统用户kk
```

为新添加的用户指定/home目录

```
# useradd-d /home/myf kk //新添加用户kk，其home目录为/home/myf
//当用户名kk登录主机时，系统进入的默认目录为/home/myf
```



## 设置密码

 创建的用户还没有设置登录密码，需要利用`passwd`进行密码设置

```text
asswd [options] [username]
```

`option` 参数有如下：

- -d 删除密码
- -f 强迫用户下次登录时必须修改口令
- -w 口令要到期提前警告的天数
- -k 更新只能发送在过期之后
- -l 停止账号使用
- -S 显示密码信息
- -u 启用已被停止的账户
- -x 指定口令最长存活期
- -g 修改群组密码
- 指定口令最短存活期
- -i 口令过期后多少天停用账户

例如，修改用户密码

```
# passwd runoob  //设置runoob用户的密码
Enter new UNIX password:  //输入新密码，输入的密码无回显
Retype new UNIX password:  //确认密码
passwd: password updated successfully
# 
```

显示账号密码信息

```
# passwd -S runoob
runoob P 05/13/2010 0 99999 7 -1
```

删除用户密码

```
# passwd -d lx138 
passwd: password expiry information changed.
```



### 修改用户

`chage` 命令用来修改与用户密码相关的过期信息，如密码失效日、密码最短保留天数、失效前警告天数等

```text
chage [option] [username]
```

常见的参数有：

- -d：指定密码最后修改日期

- -E：密码到期的日期

- -l：列出用户以及密码的有效期

- -m：密码能够更改的最小天数
- -M：密码保持有效的最大天数





### 删除用户

userdel 命令用来删除用户的相关的所有数据。

```text
userdel [options] [username]
```

常见的参数有：

- -r：删除用户登入目录以及目录中所有文件

例如删除用户账号

```
# userdel hnlinux
```







用户组相关的操作如下：

### 新增用户组

`groupadd`用于创建一个新的工作组，新工作组的信息将被添加到系统文件中

```text
groupadd [options] [groupname]
```

常见的参数有如下：

- -g：指定新建工作组的 id；
- -r：创建系统工作组，系统工作组的组ID小于 500
- -K：覆盖配置文件 "/ect/login.defs"
- -o：允许添加组 ID 号不唯一的工作组
- -f,--force: 如果指定的组已经存在，此选项将失明了仅以成功状态退出

例如创建一个新的组，并添加组 ID。

```
＃groupadd －g 344 runoob
```





### 修改用户

`groupmod `命令用来修改 `group `相关的参数，例如群组识别码或者名称

```text
groupmod [options] [groupname]
```

常见的参数有：

- -g <群组识别码> 　设置欲使用的群组识别码
- -o 　重复使用群组识别码
- -n <新群组名称> 　设置欲使用的群组名

例如修改组名：

```
# groupmod -n linux linuxso 
```





### 删除用户组

`groupdel` 用于删除用户组，如果该群组中仍包括某些用户，则必须先删除这些用户后，方能删除群组

```text
groupdel [groupname]
```



日常工作通常会碰到只有` root `用户才有权限执行的操作，这就需要使用用户身份切换的命令：

### su

用于变更为其他使用者的身份，除 `root` 外，需要键入该使用者的密码







### sudo

`sudo`命令以系统管理者的身份执行指令，也就是说，经由 sudo 所执行的指令就好像是 root 亲自执行

不是所有的用户都能执行 `sudo` 命令的，而是在 `/etc/sudoers` 文件内的用户才能执行这个命令

例如`sudo`命令使用`ls`：

```
$ sudo ls
```



## 参考文献

- https://zhuanlan.zhihu.com/p/37964411
- https://zhuanlan.zhihu.com/p/105482468