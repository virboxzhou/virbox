# Python 加密流程

### 背景：

目前软件开发商对 Python 加密时可能会有两种形式，一种是对 python 转成的 exe 进行保护，另一种是直接对 .pyc 文件进行保护，下面将列举两种形式的保护流程。

### 使用 Virbox Protector 加壳工具

Virbox Protector 是北京深思数盾自主研发的加壳工具，对于 Python 的保护方式主要是对 Python 转成的 exe 和 .pyc 进行加密保护

从 Virbox 开发者工具盒打开加壳工具，将待加密软件拖入到加壳工具中

注：使用加壳工具的前提是点击“下载” SDK，并安装

![](/assets/import100.png)

加壳工具目前支持对可执行 exe 和 dll 加壳，支持的开发语言以及开发框架：

C、C++、.Net、VB6.0、Deliph、Java、ARX插件、Revit\(插件\)、Unity3D、UE4、PHP、Labview、Mathlib、Python、Lua、VF、go、Perl、Revit软件中所有格式得资源文件、视频、音频PPT、游戏资源

### **对Python转exe加壳**

将 demo.exe 拖入到加壳工具中，然后设置加壳工具。

![](/assets/import102.png)

### 设置加壳工具

**登录云锁**：

即登录[ Virbox LM ](https://developer.lm.virbox.com/login.jsp)平台开发者账号

**许可形式：**

勾选相应许可形式![](/assets/import104.png)

此处勾选的许可形式需要与发布给用户的许可类型一致，[四种许可类型简介](/Virbox/si-zhong-xu-ke-jian-jie.md)

**许可 ID：**

许可 ID 需要自定义，是 1-42 亿数字范围。

许可 ID 是加密过程中需要使用的一个重要概念，是加密后软件和授权唯一的标识，也可以代表软件开发商的一个产品或者一个模块，许可 ID 在下一步的发布许可中会直接用到。

**API密码：**

进入 Virbox LM 开发者平台，页面顶部点击“查看”，将API密码输入至此![](/assets/import107.png)

**锁序列号：**

如果输入锁序列号，则加壳后的程序只有此锁可用。\(此功能只针对硬件锁\)

**被保护函数列表：**

点击“+”按钮：图对加壳前的软件进行预分析，建议对比较重要的函数选择碎片代码的保护方式，开发者需要在软件性能与安全之间平衡，如果对调用次数过多的函数选择碎片化保护，可能会影响软件的运行速率，调用次数过多的函数建议使用不保护的方式。

![](/assets/import108.png)

**加密选项：**

名称混淆：修改函数方法的名称

压缩：勾选压缩后

1、加壳后的软件不会在原文件的基础上大很多

2、软件更安全，此压缩为带密码的压缩。

生成日志：勾选后，运行加壳后的软件会生成 log 文件

后台检测时间间隔（秒）：设置心跳时间，检测当前 session 是否可用。

附加数据-扩展模块：程序带有附加数据，因 Python 转为 exe 的工具不同，所系加壳工具选项可能会有不同，如有此选项，则需要勾选此选框。

插件：加壳无需设置插件功能

![](/assets/pythontuozhan01.png)

**消息选项：**

设置许可失效时提示的形式、设置提示标题、软件剩余时间、剩余次数以及其他提示消息

![](/assets/import113.png)

### **软件加壳：**

设置好相应的选项后，点击加壳按钮，对软件进行加壳保护

![](/assets/import116.png)

### 加密后文件

加密前的软件

![](/assets/pythonprot01.png)

加密后的软件![](/assets/pythonprot02.png)

①加壳前的软件原文件 xxx.exe，将此文件剪切备份至其他文件夹

②加壳后的配置文件 xxx.exe.ssp，此配置文件主要记录 API 密码和一些配置信息，可删除。

③加壳后的软件 xxx.ssp.exe，建议将加壳后的软件名称修改为原文件名称。

### **对 .pyc 加密**

### 首先对安装 Python 路径下的 python.exe 进行加密

使用加壳工具对 Python 安装目录下的 python.exe 进行加壳，将 python.exe 拖入到加壳工具 Virbox Protector 中

![](/assets/pythonexepro01.png)

![](/assets/pythonexevirbox.png)

**登录云锁**：

即登录 [Virbox LM 平台](https://developer.lm.virbox.com/login.jsp)开发者账号

**许可形式：**

勾选相应许可形式![](/assets/import104.png)

此处勾选的许可形式需要与发布给用户的许可类型一致，四种许可类型简介（加入链接）

**许可 ID：**

许可 ID 需要自定义，是 1-42 亿数字范围。

许可 ID 是加密过程中需要使用的一个重要概念，是加密后软件和授权唯一的标识，也可以代表软件开发商的一个产品或者一个模块，许可 ID 在下一步的发布许可中会直接用到。

**API密码：**

进入 Virbox LM 开发者平台，页面顶部点击“查看”，将API密码输入至此![](/assets/import107.png)

**锁序列号：**

如果输入锁序列号，则加壳后的程序只有此锁可用。\(此功能只针对硬件锁\)

**“被保护函数列表”：**选项中，按照默认选项即可，不需要做任何设置

**“加密选项”：**“设置选项”无需勾选任何选框，将“插件”中ds功能打开，输入密码即可。

![](/assets/pythonproselect.png)

**“消息选项”：**设置许可失效时的提示形式、设置提示标题、软件剩余时间、剩余次数以及其他提示消息

![](/assets/pythonpronew.png)

点击“立即加壳”，加壳后会额外生成图示两个文件

![](/assets/pythonexepro02.png)

python.exe.ssp 是配置文件，在后面对 .py/.pyc 加密时会用到

python.ssp.exe 是加壳后的 python.exe 文件，将 python.exe  剪切到其他文件夹备份，python.ssp.exe 名字改为 python.exe 即可。

### 对.pyc进行加密

在开发者工具盒打开 DSprotector 使用 DS Protector 对 .pyc 进行保护

![](/assets/xiazaiqiopends.png)

添加上一步加密 python.exe 生成的 python.exe.ssp 文件

![](/assets/ds_select_ssp.png)

②添加要加密的 .pyc

![](/assets/python_pyc_protector.png)

③点击“保护它”，加密成功

![](/assets/python_pyc_sucess.png)

至此，Python 转 exe 或者 .pyc 文件已经加密成功，下一步需要将许可授权给软件用户，这样用户才可以使用加密后的软件。详见[发布许可流程（授权）](/xu-ke-liu-cheng.md)

