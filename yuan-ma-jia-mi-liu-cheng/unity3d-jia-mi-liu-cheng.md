# Unity 3D 加密流程

### 使用 Virbox Protector 加壳工具

Virbox Protector 是北京深思数盾自主研发的加壳工具，对于 Unity 的保护方式主要是对 Assembly-CSharp.dll 进行加密保护。

从 Virbox 开发者工具盒打开加壳工具，将待加密软件拖入到加壳工具中

注：使用加壳工具的前提是点击“下载” SDK，并安装

![](/assets/import100.png)

![](/assets/import102.png)

加壳工具目前支持对可执行 exe 和 dll 加壳，支持的开发语言以及开发框架：

C、C++、.Net、VB6.0、Deliph、Java、ARX插件、Revit\(插件\)、Unity3D、UE4、PHP、Labview、Mathlib、Python、Lua、VF、go、Perl、Revit 软件中所有格式得资源文件、视频、音频 PPT、游戏资源

本示例主要以 Unity3D 项目中 Assembly-CSharp.dll 进行加密保护，Unity3D 项目结构图如下：

![](/assets/import135.png)

![](/assets/import136.png)

将 Assembly-CSharp.dll 拖入到加壳工具中，然后设置加壳工具。

### 设置加壳工具

![](/assets/import138.png)

**登录云锁**：

即登录 Virbox LM 平台开发者账号

**许可形式：**

勾选相应许可形式       ![](/assets/import106.png)

此处勾选的许可形式需要与发布给用户的许可类型一致，[四种许可类型简介](/Virbox/si-zhong-xu-ke-jian-jie.md)

**许可 ID：**

许可 ID 需要自定义，是 1-42亿 数字范围。

许可 ID 是加密过程中需要使用的一个重要概念，是加密后软件和授权唯一的标识，也可以代表软件开发商的一个产品或者一个模块，许可 ID 在下一步的发布许可中会直接用到。

**API密码：**

进入 Virbox LM 开发者平台，页面顶部点击“查看”，将API密码输入至此![](/assets/import107.png)

**锁序列号：**

如果输入锁序列号，则加壳后的程序只有此锁可用。\(此功能只针对硬件锁\)

**被保护函数列表:**

![](/assets/import110.png)主要是对可执行 exe 文件加壳前进行预分析，因对 Unity3D 加密方式不同，所以此处不做设置

**加密选项：**

可设置加密后文件输出的位置

可设置后台检测时间：表示每隔多少秒对运行程序进行检测是否存在对应许可，如果没有那么就会提示错误，或者退出。如果后台检测时间设为 0s, 那么后台就不会进行检测许可的操作。

插件功能主要用于 Unity3D 资源文件保护时使用，此处默认关闭

**消息选项：**

设置许可失效时提示的形式、设置提示标题、软件剩余时间、剩余次数以及其他提示消息

![](/assets/import113.png)

**软件加壳：**

设置好相应的选项后，点击加壳按钮，对软件进行加壳保护

![](/assets/import140.png)

### 加密后文件

加密前的软件

![](/assets/import142.png)

加密后的软件

![](/assets/import143.png)

①加壳前的软件原文件 xxx.exe，将此文件剪切备份至其他文件夹

②加壳后的配置文件xxx.dll.ssp，此配置文件主要记录 API 密码和一些配置信息，可删除。

③加壳后的软件xxx.ssp.dll，建议将加壳后的软件名称修改为原文件名称。

至此使用加壳工具加密的过程已经完成，下一步根据不同用户的不同需求发布不同的许可内容到用户的账号中,详见[发布许可流程（授权）](/xu-ke-liu-cheng.md)

