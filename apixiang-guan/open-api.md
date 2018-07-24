# Open API

## Open API

Open API 是 Virbox LM 提供给开发者调用的 API ，它面向的是开发者，而不是最终用户，需要开发者自己通过提供的 API 来完成用户注册，许可发布等操作。

## API 概览

|  | **API** | **描述** |
| :--- | :--- | :--- |
| **用户相关** | addUser | 添加普通用户 |
|  | addShadowUser | 添加影子账号 |
|  | modifyUserPasswd | 修改影子账号的密码 |
|  | modifyUser | 修改用户备注信息 |
|  | deleteUser | 删除用户（包含普通用户和影子账号） |
|  | findUsers | 查找用户 |
| **产品相关** | addProduct | 添加产品 |
|  | modifyProduct | 修改产品信息 |
|  | getProductInfo | 按照许可产品许可ID获得产品信息 |
|  | productList | 按照产品名称模糊搜索产品信息 |
|  | deleteProduct | 按照产品许可ID删除产品 |
| **模板相关** | addTemplate | 添加模板 |
|  | modifyTemplate | 修改模板信息 |
|  | templateList | 按照产品许可ID枚举模板 |
|  | findTemplate | 按照模板编号查找模板信息 |
|  | deleteTemplate | 删除模板 |
| **云锁与软锁许可相关** | issueLicenseByProduct | 不依赖模板发布许可 |
|  | issueLicenseByPloy | 可修改许可策略的发布许可 |
|  | issueLicense | 不可修改许可策略的发布许可 |
|  | updateLicense | 更新（修改）已发许可 |
|  | deleteLicense | 删除许可 |
|  | licenseList | 搜索许可 |
|  | softLockbindList | 获取软锁的绑定机器信息 |
|  | softLockUnbind | 解绑软锁 |
| **硬件锁许可相关** | devicelicense/addlic | 签发添加许可升级包 |
|  | devicelicense/updatelic | 签发更新许可升级包 |
|  | devicelicense/dellic | 删除硬件许可升级包 |
|  | devicelicense/ctrllic | 签发控制许可升级包 |
| **标签管理相关** | addTag | 添加标签 |
|  | updateTag | 修改标签 |
|  | deleteTag | 删除标签 |
|  | findTags | 按标签名称查找标签 |

## 术语

普通用户：必须用邮箱或手机号作为登录账号，云平台全局可用，可使用不同开发者发布的许可，此类账号可以在终端自助登录云平台的中间件来使用许可软件；

影子账号：账号由创建该账号的开发者管理，仅用于跟开发者自己的账号系统建立关联，此类账号由开发者应用自己管理登录过程；

llicense ID：产品在深思云平台的产品许可ID，取值范围为\[1-\(2^32-1\)\]；

三区数据：为开发者提供三个数据存储区域，可以存储任意数据：

**rom**：在建产品或模板时可以写进去，在许可使用过程中不能修改，最大65535 byte；

**raw**：在建产品或模板时可以写进去，在许可使用过程中可以修改，最大65535 byte；

**pub**：在建产品或模板时可以写进去，在许可使用过程中不能修改，最大65535 byte；

## 接口概述

请求结构：

**服务接口地址为**：[https://openapi.senseyun.com/v2/sv/{$请求操作}](https://openapi.senseyun.com/v2/sv/{$请求操作})

**通信协议**：HTTPS。

**请求方法**：仅支持HTTP POST方法,接口调用时ContentType必须设置成"application/json"。

**请求参数**：每个接口地址中服务接入地址后边的代表请求的操作，以及每个操作都需要包含的公共请求参数和指定操作所特有的请求参数。

**字符编码**：请求及返回结果都使用 UTF-8 字符集进行编码。

**请求结构：**JSON

**返回结构：**JSON  
**成功结果：**HTTP请求返回2xx, 同时返回 json 中 code 属性值为0.

**错误结果：**当调用出现异常，HTTP请求返回 4xx 或 5xx，返回结构内容忽略。

如果为业务逻辑方面的错误，HTTP请求仍返回 2xx,但返回json中code属性值为非0值，desc属性值为错误说明。

## 公共参数：

**公共请求参数**

需要将所有的公共请求参数放在HTTP header中：

| **参数名称** | **参数类型** | **是否必填** | **描述** |
| :--- | :--- | :--- | :--- |
| SenseAppID | 字符串 | Y | 在开发者网站登录后可以查看到SenseAppID |
| SenseTimestamp | 字符串 | Y | 1970年01月01日00时00分00秒起至现在的总毫秒数，和服务器相差时间超过30分钟，API将返回授权失败； |
| SenseNonce | 字符串 | Y | 唯一识别码，用于一段时间内防重放\(每次需传入不重复的值，例如UUID\)； |
| SenseSign | 字符串 | Y | 用于安全验证的签名值，签名过程参见第三节 |

