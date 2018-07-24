# Java 加密流程

## 背景：

Java 开发语言以其安全性高、代码优化、跨平台等特性，迅速取代了很多传统高级语言，占据了企业级网络应用开发等诸多领域的霸主地位。特别是近年来大数据、互联网+、云计算技术的不断发展，Java 开发语言更具有不可替代的地位。

不过，Java 最突出的跨平台优势使其要以中间代码的形式运行在虚拟机环境中，因此 Java 代码反编译要比其他开发语言更容易实现，并且反编译的代码经过优化后几乎可与源代码相媲美。为了避免出这种情况，保护软件知识产权，有一种叫做 Java 混淆器的工具被开发出来。

但 Java 混淆器的作用是对编译好的代码进行混淆，使得反编译后的代码混乱难懂，真正起的作用只是增加了逆向工程的难度，最终结果也是治标不治本，对于一些掌握工具的人来说几乎还是透明的。另外由于 Java 程序中会有多重映射关系，因此大多数混淆工具的兼容性会很差。

以下为 Virbox 云/软许可加密 Java 项目流程

## 部署项目并启动服务

### 项目部署

项目放在 webapps 目录下,先启动 tomcat 服务确认能正常启动，启动过后该 War 包会自动解压出一个同名的文件夹

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/java_put.png)

### 启动 tomcat 服务

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/java_start_tomcat.png)

### 找到依赖的 java.exe

服务启动成功后,进入任务管理器-服务-找到目前运行项目所依赖的 jdk , 进入目录找到对应程序 进行加密. 如下图

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/java_protect_exer.png)

## 使用 Virbox Protector 加壳工具

### 打开 virboxprotector.exe对 java.exe 进行加壳

从 Virbox 开发者工具盒打开加壳工具，将待加密软件拖入到加壳工具中

注：使用加壳工具的前提是点击“下载” SDK，并安装。

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/import100.png)

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/import102.png)

加壳工具目前支持对可执行 exe 和 dll 加壳，支持的开发语言以及开发框架：

C、C++、.Net、VB6.0、Deliph、Java、ARX插件、Revit\(插件\)、Unity3D、UE4、PHP、Labview、Mathlib、Python、Lua、VF、go、Perl、Revit 软件中所有格式得资源文件、视频、音频PPT、游戏资源

## 设置加壳工具

将找到依赖的 java.exe 步骤中的 java.exe 添加到加壳工具中 , 如下图所示。

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/java_virbox_exe1.png)

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/java_virbox_exe2.png)

**登录云锁**：

即登录 Virbox LM 平台开发者账号

**许可形式：**

勾选相应许可形式![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/import104.png)

此处勾选的许可形式需要与发布给用户的许可类型一致，[四种许可类型简介](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/Virbox/si-zhong-xu-ke-jian-jie.md)

**许可 ID：**

许可 ID 需要自定义，是 1-42 亿数字范围。

许可 ID 是加密过程中需要使用的一个重要概念，是加密后软件和授权唯一的标识，也可以代表软件开发商的一个产品或者一个模块，许可 ID 在下一步的发布许可中会直接用到。

**API密码：**

进入 Virbox LM 开发者平台，页面顶部点击“查看”，将API密码输入至此![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/import107.png)

**锁序列号：**

如果输入锁序列号，则加壳后的程序只有此锁可用。\(此功能只针对硬件锁\)

**被保护函数列表：**此处不需要做设置

**加密选项：**

名称混淆：无需勾选

压缩：无需勾选

**输出文件**：输出文件，可以修改程序保护后生成文件的路径和名称。

注意： 1 、如果只有文件名称，那么路径为源程序的路径；

2、如果输出文件名和源文件同名，生成的程序会将源程序覆盖；

**生成日志：**生成 virboxprotector 的工作日志，方便出错的时候排查问题。正常情况下您可不选，只 有在加壳后的程序运行出现问题的时候，您需要选择并将生成的日志发给深思技术人员进行排查问题。

**后台检测时间间隔 \( 秒 \)：**后台检测时间间隔（秒），表示每隔多少秒对运行程序进行检测是否存在对应许可，如果没有那么就会提示错误，或者退出。如果后台检测时间设为 0s, 那么后台就不会进行检测许可的操作。

**插件**：主要用于对 class 资源进行加密，请务必打开.密码可随意设置或者使用默认。

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/java_protect_select.png)

**消息选项**

设置许可失效时的提示形式、设置提示标题、软件剩余时间、剩余次数以及其他提示消息

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/java_protect_new.png)

**软件加壳**

设置好相应的选项后，点击加壳按钮，对软件进行加壳保护

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/java_virbox_jiake.png)

提示：点击运行加密时如果出现如下问题，请先把 java.exe 拷贝到其它盘符再加密。然后再拷贝到jdk目录下。

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/java_noright.png)

加密成功后会生成两个文件 java.exe.ssp、java.ssp.exe ，把原来的 java.exe 剪切备份，把 java.ssp.exe 修改成 java.exe 文件。 （ java.ssp.exe 是加密的）如下图。

## 加密后文件

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/javaexe_aftprot.png)

① java.exe 加壳前的软件原文件

② java.exe.ssp 加壳后的配置文件，此配置文件主要记录一些配置信息,下一步在加密资源文件会继 续使用

③ java.exe.ssp 加壳后的软件，建议将加壳后的软件名称修改为原文件名称

## 对 class文件加密

### 打开 DSProtector.exe对 .class、.jar 或者 .xml 资源进行加密

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/xiazaiqiopends.png)

### 添加 java.exe.ssp

点击浏览添加 java.exe.ssp 文件。

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/java_ssp_pro.png)

### 4.5.3 添加需要保护的资源

在 tomcat webapps 目录下 找到项目添加要保护的 .class 、.jar 或者 .xml 进行加密. 点“保护它”,即可完成加密，支持多选。

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/java_class_pro.png)

如果点“保护它” 出现了如下错误,只需把要要加密的 class 拷贝到其它盘符再重新添加资源 并保护它,把生成的文件再次拷贝到原 class 目录下。

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/java_pro_mistake.png)

至此使用加壳工具加密的过程已经完成，下一步根据不同用户使用的不同需求创建授权模板，比如控制此 java 程序用户可以使用多长时间，详见[发布许可流程（授权）](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/xu-ke-liu-cheng.md)。

