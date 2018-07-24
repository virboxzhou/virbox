# UE4 加密流程

使用 Virbox Protector 加壳工具

Virbox Protector 是北京深思数盾自主研发的加壳工具，对于 UE4 的保护方式主要是对发行模式下 xxx.exe 进行保护

从 Virbox 开发者工具盒打开加壳工具，将待加密软件拖入到加壳工具中

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/import100.png)

加壳工具目前支持对可执行 exe 和 dll 加壳，支持的开发语言以及开发框架：

C、C++、.Net、VB6.0、Deliph、Java、ARX 插件、Revi t\(插件\)、Unity3D、UE4、PHP、Labview、Mathlib、Python、Lua、VF、go、Perl、Revit软件中所有格式得资源文件、视频、音频 PPT、游戏资源

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/import102.png)

本示例主要以 UE4 项目中发行模式下的 xxx.exe 进行加密保护，UE4项目结构图如下：

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/importUE4mulu.png)

将 xxx.exe 拖入到加壳工具中，然后设置加壳工具。

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/importUE4.exeprot.png)

设置加壳工具

**登录云锁**：

即登录 Virbox LM 平台开发者账号

**许可形式：** 

勾选相应许可形式![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/import104.png)

此处勾选的许可形式需要与发布给用户的许可类型一致

**许可ID：**

许可 ID 需要自定义，是 1-42 亿数字范围。

许可 ID 是加密过程中需要使用的一个重要概念，是加密后软件和授权唯一的标识，也可以代表软件开发商的一个产品或者一个模块，许可 ID 在下一步的发布许可中会直接用到。

**API密码：**

进入Virbox LM 开发者平台，页面顶部点击“查看”，将API密码输入至此![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/import107.png)

**锁序列号：**

如果输入锁序列号，则加壳后的程序只有此锁可用。\(此功能只针对硬件锁\)

**被保护函数列表:**

对加壳前的软件进行预分析，建议对比较重要的函数选择碎片代码的保护方式，开发者需要在软件性能与安全之间平衡，如果对调用次数过多的函数选择碎片化保护，可能会影响软件的运行速率，调用次数过多的函数建议使用不保护的方式

**加密选项：**

建议对exe文件勾选压缩和导入表保护选项：勾选压缩后软件更安全，此压缩为带密码的压缩。

可设置加密后文件输出的位置

可设置后台检测时间：表示每隔多少秒对运行程序进行检测是否存在对应许可，如果没有那么就会提示错误，或者退出。如果后台检测时间设为 0 s,那么后台就不会进行检测许可的操作。

插件功能主要用于 UE4 资源文件保护时使用，此处默认关闭

**消息选项：**

设置许可失效时提示的形式、设置提示标题、软件剩余时间、剩余次数以及其他提示消息

**软件加壳：**

设置好相应的选项后，点击加壳按钮，对软件进行加壳保护

## 加密后文件

加密前的软件

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/importprote01UE4exe.png)

加密后的软件

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/importprot02UE4exe.png)

①加壳前的软件原文件xxx.exe，将此文件剪切备份至其他文件夹

②加壳后的配置文件 xxx.exe.ssp，此配置文件主要记录API密码和一些配置信息，可删除。

③加壳后的软件 xxx.ssp.exe，建议将加壳后的软件名称修改为原文件名称。

至此使用加壳工具加密的过程已经完成，下一步根据不同用户的不同需求发布不同的许可内容到用户的账号中,详见[发布许可流程（授权）](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/xu-ke-liu-cheng.md)

