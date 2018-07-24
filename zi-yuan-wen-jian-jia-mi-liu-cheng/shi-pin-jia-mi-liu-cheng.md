# 视频加密流程

## 视频加密流程

### 获取支持加密视频类型的加壳工具

从 [Virbox 开发者工具盒](../virboxtools/virbox-kai-fa-zhe-gong-ju-he.md)中获取

### 在网上找到一款绿色免安装版视频播放软件

建议挑选不会报毒的软件，本文以 PotPlayer 播放软件为例（声明：本文仅做案例展示，如涉及商业问题，深思概不负责~）

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/shipin01.png)

## 视频加密指引

### 打开加壳工具

从 Virbox 开发者工具盒中打开加壳工具，对绿色免安装版视频播放器的 .exe 进行加壳

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/import145.png)

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/shipinjiake.png)

### 选择对应加密类型

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/jiake002.png)

### 输入许可 ID

输入许可 ID，此许可 ID 可以代表一个视频文件，许可 ID 的范围是 1-42 亿数字范围

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/jiekeID.png)

### 输入 API 密码

此密码可以通过云开发者平台获取 [https://developer.lm.virbox.com/login.jsp](https://developer.lm.virbox.com/login.jsp)

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/jiake04.png)

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/jiake005.png)

### 设置加密选项

输入 ds 密码：此密码长度没有限制，主要作用是增加软件的安全强度.

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/jiake006.png)

将绿色免安装版视频播放器的可执行 exe 拖入到加壳工具中

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/jiake008.png)

注意文件输出路径，此绿色免安装版视频播放器有依赖项，所以输出路径依然选择在原文件路径下

点击立即加壳

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/jiake009.png)

加密后的软件会额外生成两个文件，PotPlayerMini.ssp.exe（加密后的视频需要使用此软件打开）与 PotPlayerMini.exe.ssp（下一步用于视频加密）

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/jiake010.png)

### 启动 DS 工具，对视频进行保护

打开Virbox 开发者工具盒，点击启动 DS 工具

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/xiazaiqiopends.png)

选中上一步生成的 PotPlayerMini.exe.ssp 文件

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/jiake012.png)

添加视频文件

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/jiake013.png)

点击保护

![](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/assets/jiami014.png)

至此，视频已经加密成功，下一步将相应授权发布到“用户账号”中

注：加密后的视频只能使用加壳后的播放器播放，使用加壳后的 PotPlayerMini.ssp.exe 打开，加密后的视频文件（加密后的文件名为原视频文件名称，原视频文件以--文件名 .bak 备份保存）

发授权流程——[许可流程](https://github.com/virboxzhou/virbox/tree/d12a4b0aefdf309f6422c723bf65ac059fb84ea4/xu-ke-liu-cheng.md)

