# PPT 加密流程

## **步骤：**

1、PPT 文档转换为可执行 exe 文件

2、对生成的 exe 可执行文件进行加密

## **加密流程** {#PPT文档转换为可执行exe加壳指引-加密流程}

1. PPT 文档转换为可执行 exe 文件（本处以 2345 好压 PPT 转换 exe 为例）

   ①把要转换的 PPT 文件另存为“PowerPoint 放映”，后缀名为 pps 或 ppsx

   ![](http://help.sense.com.cn/wp-content/uploads/2018/03/1.png)

   ②在得到的文件上面点击鼠标右键，单击“添加到压缩文件（A）…”如图

   ![](http://help.sense.com.cn/wp-content/uploads/2018/03/2.png)

   ③在压缩文件格式中选择“7Z”，选择右边“压缩选项”中的“创建固实压缩文件”和“创建自解压格式”，并将文件名改为自己的文件名，注意，后缀必须是“exe”，如图

   ![](http://help.sense.com.cn/wp-content/uploads/2018/03/3.png)

   ④单击“自解压选项” 单击“模式”选项卡，按图示选择对应选项

   ![](http://help.sense.com.cn/wp-content/uploads/2018/03/4.png)

   ⑤单击“解压”选项卡，在“解压后运行”中填写刚PPT另存的名称，注意一定要带后缀名

   ![](http://help.sense.com.cn/wp-content/uploads/2018/03/5.png)

   点击确定，立即压缩，即可生成 exe 可执行文件

2. 对生成的 exe 可执行文件进行加密（此处以硬件锁为例，使用加壳工具进行加密，具体的云锁、软锁和硬件锁的授权和加密的流程请参考指引）  
    ①打开 Virbox Protector 执行文件，将可执行 exe 文件拖进去进行保护，填写相应的许可形式和许可 ID，开发商 API 密码（在云平台开发者信息处查看），点击立即加壳

   ![](/assets/jiake002.png)

   ②加壳完成后默认在同目录下生成一个和源文件名称相同的 .ssp.exe，没有锁插入或者没有授权之后的账号时的状态:

   ![](http://help.sense.com.cn/wp-content/uploads/2018/03/7.png)

   有锁插入或者登陆授权之后的用户账号 PPT 可以正常打开。



