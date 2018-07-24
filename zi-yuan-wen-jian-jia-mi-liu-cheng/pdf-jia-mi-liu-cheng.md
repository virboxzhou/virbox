# PDF 加密流程

## **注册 Virbox LM 帐号**

注册地址：[https://developer.lm.virbox.com/reg.html](https://developer.lm.virbox.com/reg.html)

## **获取工具**

### 下载安装开发 SDK

登录 Virbox LM，提交转正，通过后点击下载，可安装 [Virbox 开发者工具盒](../virboxtools/virbox-kai-fa-zhe-gong-ju-he.md)，工具盒中包含 加壳工具及 DS 加壳工具

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/virbox_zhuanzhan.png)

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/virbox_sdk.png)

## 登录 Virbox LM 平台，按以下步骤操作：

1、获取API 密码，加壳时会用到；

2、添加产品，产品添加后会得到一个许可ID，加壳时用到；

3、创建销售模版，发许可时用这个模版，可创建永久类型、限时限次类型等；

4、 添加用户帐号（手机号或者邮箱），打开加壳后的软件需要用此用户帐号登录 Virbox 用户工具；

5、给用户帐号发布许可（可以用注册的开发者账号测试）。加壳后需在 Virbox 用户工具登陆用户账号，检测许可正常才能打开加密后的程序，这一步就是发许可。

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/pdf003.png)

## **加密 PDF 阅读工具：SumatraPDF.exe**

打开 SDK 中的加壳工具，将 SumatraPDF.exe 拖到加壳工具中，右上角登录云锁；

许可配置：许可形式勾选云锁或者软锁，填写许可 ID 及 API 密码（步骤3中登陆 Virbox LM 获取），注意下图中的几处：

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/pdf004.png)

加密选项设置：将 ds 插件打开，点击立即加壳，PDF 阅读器加密完成。

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/PDF005.png)

## 使用 DS Protector 对 PDF 文件加密

打开 DS Protector，将 SumatraPDF.exe.ssp 拖入进来.对 PDF 阅读工具 SumatraPDF.exe 加密时，生成 SumatraPDF.exe.ssp

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/pdf008.png)

点击添加资源，选择所需加密 PDF 文件加入，点击保护它，完成后退出，可批量添加多个 PDF 文件.

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/pdf009.png)

至此加密完成，登录 Virbox 用户工具即可打开加密后的 PDF 文件

