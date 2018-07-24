# Virbox LM 发布许可流程

# 产品管理

深思使用产品对应开发者的应用程序，使用模板来定制许可方式。对于一个被用户使用的产品来说，许可是开发者软件与用户沟通的核心媒介，开发者负责给指定用户发布许可，而被签发的用户按照许可约定的方式使用软件。

一个开发者可能具有多款软件需要保护或者授权分发（深思称为许可分发），建议这种工作是从使用初期就进行良好的规划，避免造成混乱。开发人员或者管理人员的流失一定程度上也会影响后期方案的维护及管理，所以从加密开始就完成产品的管理是非常重要的。

支持设定的产品属性如下：

| 产品属性 | 描述 |
| :--- | :--- |
| 许可 ID（LicenseID） | 产品创建时必须关联许可ID作为对应唯一产品的标识信息。 |
| 产品名称 | 定义产品名称 |
| 显示名称 | 显示在端的名称 |
| 许可形式 | 区分产品可使用的许可形式，分为云锁与软锁，分别对应于不同使用场景。 软锁：将许可存储到本地后可离线使用，用户只需定期联网激活即可。 |
| 产品logo | 开发者上传产品logo，可在端展示。上传的logo仅支持png格式，长宽限制为160\*120像素。需要将40\*40与120\*120像素的两个logo按照示例在本地合成一张图上传。 注：DEMO开发者，在云平台上传产品信息，在SS端不生效。 |
| 产品简介 | 产品简介信息，100字以内。 |
| 用户数据区 | 数据区分为只读区、读写区和公开区，分别对应不同的访问属性，适应不同的使用场景。 |
| 模块 | 将产品的功能定义为不同模块，适应于不同模块分别发布许可的场景。 ID：模块的标识信息，在产品内唯一，一个产品最多可创建64个模块。 名称：模块的名称，命名模块方便区分。 删除产品中模块时，基于此产品建立的模板中的模块也会相应删除。 |

## 新建产品

1. 打开产品管理，点击"新建"，填写产品信息;
2. 选择产品的许可形式，这决定了之后使用该产品建模板及发许可时可选择的许可类型;
3. 根据需要，上传产品 logo、定义用户数据区及其他信息;
4. 高级属性中可定义用户数据区，模块及其他信息
5. 点击“确定”，保存产品信息。

![](/assets/newproductor.png)

## 编辑产品

1. 查看产品列表，选中产品右侧的编辑按钮，进入信息编辑页面修改产品信息;
2. 按照新建产品的规则修改产品信息，License ID 一旦创建无法修改;
3. 若使用该产品创建过模板，则修改该产品后需要同时修改模板，否则模板可能失效。

![](https://developer.lm.virbox.com/course/images/course/deve_pros.png "编辑产品")

## 查看产品

查看产品列表，选中产品右侧的查看按钮，进入产品详情页面查看产品信息。

![](https://developer.lm.virbox.com/course/images/course/view_pros.png "查看产品")

## 删除产品

1. 查看产品列表，选中产品右侧删除按钮。删除前需要先确定有无依据此产品建立的模板。
2. 若无依赖的模板，可直接删除；若存在依赖的模板，产品不可删除，请先删除关联模板。。

![](https://developer.lm.virbox.com/course/images/course/delete-product.png "删除产品")

# 模板管理 {#template-management}

不同类型许可具有近似特征，重复操作一类许可不仅浪费时间，还会出现操作失误，不利于产品的管理和许可签发。深思使用模板的方式固化常用的许可类型，一次设定、反复使用，来减少开发者的工作量，提高效率。

## 支持设定的模板属性如下：

| 模板属性 | 描述 |
| :--- | :--- |
| 模板名称 | 定义模板名称 |
| 产品选择 | 选择与该模板关联的产品，设置的模板属性对该产品生效。 |
| 许可形式 | 区分产品可使用的许可形式，分为云锁与软锁，分别对应于不同使用场景。此处取决于该模板关联的产品在创建时设定的许可形式。 |
| 许可类型 | 许可类型包括普通许可与试用许可，普通许可包含按天计费，按年计费，一次性计费三种计费模式；试用许可无计费模式，最多允许发布90天，绑定设备数固定为5. |
| 计费模式 | 计费模式包括按天计费（0.1元/天）按年计费（15元/年）和一次性计费（58元）。 |
| 时间限制 | 时间限制有两种类型： 1、具体时间：设置明确的起止时间或终止时间，到期将不可使用 2、许可发布时间作为许可开始时间：适用于使用此模板发布许可时许可开始计时的场景，结合限定时长的设置，到期将不可使用 |
| 时间跨度 | 以用户使用许可为开始时间，到期将不可使用 |
| 使用计数 | 设置有限次的使用条件，每次使用计数减少，计数归零不可使用 |
| 可离线时长 | 针对软锁，设置该许可可离线使用的时长，到期将不可使用 |
| 累积绑定设备数 | 针对软锁，设置该许可累积绑定的设备数，每次绑定计数减少，计数归零不可使用 |
| 同时绑定设备数 | 针对软锁，设置该许可同时绑定的设备数，每次绑定计数减少，计数归零不可使用 |
| 离线绑定 | 针对软锁，选择该许可是否支持离线绑定，若支持离线，则可以在Virbox用户工具中实现C2D兑换D2C，若不支持离线，兑换会提示失败 |
| 许可版本 | 针对同一产品的不同版本，通过许可版本的不同可创建不同的模板 |
| 用户数据区 | 数据区分为只读区、读写区和公开区，分别对应不同的访问属性，适应不同的使用场景。 |
| 模块 | 选择此产品已创建好的模块，选中的模块将包含在根据该模板发布的许可中 |
| 发布许可时可临时修改模板限制 | 选择此项后，基于此模板发布许可时，在保持原模板不受影响的情况下，可临时修改模板限制，包括是否永久、时间限制、时间跨度、使用计数。 |
| 发布许可时可临时修改模块选择 | 选择此项后，基于此模板发布许可时，在保持原模板不受影响的情况下，可临时修改模块选择。 |

## 新建模板

1. 打开销售模板，点击"新建"，填写模板信息。
2. 选择在产品管理处已创建的产品。
3. 根据已选择的产品定义模板的许可形式。
   a. 若选定的产品为云锁，则模板的许可形式只能为云锁；
   b. 若选定的产品为软锁，则模板的许可形式只能为软锁；
   c. 若选定的产品为云锁和软锁，则模板的许可形式既可以是软锁，也可以是云锁。
4. 许可类型和计费模式在发布许可时默认不可更改。如想修改，在高级属性中，勾选基于此模板,发布许可时是否可临时修改模板限制。如图

![](/assets/newmoban.png)

1. 高级属性中可根据需要，选择该产品创建时已定义好的模块，选择后的模块可根据模板包含在许可中。

2. 高级属性中可根据需要，选择基于此模板,发布许可时是否可临时修改模板限制。

3. 高级属性中可根据需要，选择基于此模板,发布许可时是否可临时修改模块选择。

![](https://developer.lm.virbox.com/course/images/course/new_modals.png "新建模板")

## 编辑模板

1. 查看模板列表，选中模板右侧的编辑按钮，进入信息编辑页面修改模板信息。
2. 按照新建模板的规则修改模板信息，产品一旦选择无法修改。
3. 若使用该模板发布过许可，则修改该模板后不影响已下发的许可。

![](https://developer.lm.virbox.com/course/images/course/edit-templateup.png "编辑模板")

## 查看模板

查看模板列表，选中模板右侧的查看按钮，进入模板信息页面查看模板信息。

![](https://developer.lm.virbox.com/course/images/course/cost---2.png "查看模板")

## 删除模板

1. 查看模板列表，选中模板右侧的删除按钮。
2. 若存在根据此模板发布的许可，删除后不会影响使用。
3. 点击"确定"，确认删除。

![](https://developer.lm.virbox.com/course/images/course/delete-template.png "删除模板")

## 批量删除模板

1. 查看模板列表，勾选列表左侧复选框选择需要删除的模板。
2. 若存在根据此模板发布的许可，删除后不会影响使用。
3. 点击“批量删除”，在弹出的对话框中需输入正确图片验证码。
4. 点击"确定"，确认删除。

![](https://developer.lm.virbox.com/course/images/course/delete-batch-template.png "批量删除模板")

# 用户管理 {#user-management}

开发者可以建立和管理用户，每个用户可以拥有任意多个许可。开发者可以对用户进行检索、编辑以及删除操作。用户创建成功后，邮箱信息不可变更，发布许可与用户邮箱绑定。

## 新建用户

\(1\) 添加单个用户

1. 打开用户，点击“新建用户”，可选择手机号作为账号或邮箱作为账号两种方式添加新用户。
2. 手机号作为账号添加时必须填写用户手机号信息，其他用户信息包括邮箱、性别、电话、联系地址、备注名称及描述可选填。
3. 邮箱作为账号添加时必须填写用户邮箱，其他用户信息包括手机号、性别、电话、联系地址、备注名称及描述可选填。
4. 为用户添加标签，方便开发者后续通过标签对用户进行筛选。
5. 勾选“首次登录是否需要激活”可增加对新用户的激活验证。

![](https://developer.lm.virbox.com/course/images/course/addsingle-user.png "添加单个用户")

注意：用户通过邮箱作为账号创建成功后，邮箱无法修改，通过手机作为账号创建成功后，手机号无法修改。

\(2\) 批量导入用户

1. 打开用户，点击"导入"，下载文件模板，按照文件模板格式填写用户文件。
2. 将按照正确格式填写的用户文件上传。
3. 上传成功后，可在用户列表查看已添加的用户。
4. 用户导入的任务情况可在任务管理中查看。

![](https://developer.lm.virbox.com/course/images/course/batch-importuser.png "批量导入用户")

## 编辑用户

查看用户列表，选中用户右侧的按钮，进入信息编辑页面修改用户信息。

![](https://developer.lm.virbox.com/course/images/course/edit-user.png "编辑用户")

## 查看用户

查看用户列表，选中用户右侧的查看按钮，进入用户信息页面查看用户信息。

![](https://developer.lm.virbox.com/course/images/course/view-users.png "查看用户")

## 删除用户

1. 查看用户列表，选中用户右侧的删除按钮。
2. 若对此用户发布过许可，删除用户后不会影响许可的使用。
3. 点击"确定"，确认删除。

![](https://developer.lm.virbox.com/course/images/course/delete-user.png "删除用户")

若对此用户未发布过许可，点击“确定”，确认删除。

![](https://developer.lm.virbox.com/course/images/course/delete-user1.png "删除用户")

## 批量删除用户

1. 查看用户列表，勾选列表左侧复选框选择需要删除的用户。
2. 若该用户以前给他发过许可，删除后不会影响其正常使用。
3. 点击“批量删除”，在弹出的对话框中需输入正确图片验证码。
4. 点击"确定"，确认删除。

![](https://developer.lm.virbox.com/course/images/course/delete-batch-user.png "批量删除用户")

## 导出用户

打开用户，点击"导出"，以表格格式导出当前用户列表中的所有用户。

![](https://developer.lm.virbox.com/course/images/course/export-user.png "导出用户")

## 筛选用户

打开用户，点击"筛选"，选择标签进行用户筛选，点击搜索。

![](https://developer.lm.virbox.com/course/images/course/filter-user.png "筛选用户")

# 许可分发 {#icensing-distribution}

许可分发是许可管理的核心环节，给指定用户发布许可，用户将在许可的有效期内拥有软件的使用权，到期自动终止。

## 发布许可

\(1\)单个模板发布许可

1. 打开许可分发界面，点击"发布许可"。

2. 选择已创建的模板及用户，点击"发布"。

![](https://developer.lm.virbox.com/course/images/course/cost---3.png "单个模板发布许可")

注意：若选择的模板在创建时定义为为发布许可时可临时修改模板限制，则发布许可选择该模板时可编辑模板限制，编辑模板限制下发许可不影响原模板。

若选择的模板，在创建时被定义为“发布许可时可临时修改模块选择”，则发布许可时可编辑模块选择，编辑模块下发许可，不影响原模板。

\(2\)批量发布许可

1. 打开许可分发界面，点击“批量发布”

2. 选择模板，在弹出框左侧模板列表中选择模板

3. 点击"添加选中",右侧列表中会展示出已添加的模板，可查看模板详情和移除模板

4. 点击"下一步",选择用户

![](https://developer.lm.virbox.com/course/images/course/image059.png "批量发布许可")

注意：选择模板需选择不同产品的销售模板

1. 选择用户，在弹出框左侧用户列表选择需要发布许可的用户

2. 点击“添加选中”，右侧可展示已添加的用户，可以查看用户详情和移除

3. 点击“添加全部”，添加左侧列表中全部用户，不需勾选，一次性添加用户最多不能超过1000

4. 点击“下一步”，发布许可

![](https://developer.lm.virbox.com/course/images/course/image064.png "批量发布许可")

5.选择用户时，可以通过标签筛选选择用户，点击“标签筛选”，选择标签过程中可以添加“已选标签”最多可选择5个标签

6.点击“搜索”，对弹窗左侧用户列表进行标签筛选

![](https://developer.lm.virbox.com/course/images/course/image067.png "批量发布许可")

7.选择用户时，可以通过点击“手工添加”批量添加用户，仅支持按用户名添加，多个用户之间通过换行进行分隔，一次添加用户最多不超过 1000

8.点击“添加”，对用户名进行匹配，若存在用户不存在的，将无法添加，需从新输入全部正确后，可添加成功

![](https://developer.lm.virbox.com/course/images/course/image070.png "批量发布许可")9.发布许可，弹窗左右两侧分别显示已选择的模板和已选择的用户，可查看选择用户模板和用户的详细信息

10.点击“发布”，系统会校验提交发布的数据，校验通过后离线发布许可

11.批量发布完成即可在许可列表中查看已发布的许可

12.批量发布任务的情况可通过任务管理查看

![](https://developer.lm.virbox.com/course/images/course/image075.png "批量发布许可")

## 更新许可

1. 查看许可分发列表，选中许可列表右侧的更新许可按钮

2. 在更新许可弹窗中，可对原有许可内容进行更新，更新内容根据“许可形式”和“是否永久许可”进行区分。

| 许可形式 | 是否永久 | 更新许可内容 |
| :--- | :--- | :--- |
| 软锁 | 非永久 | 开始时间 结束时间 时间跨度 可离线时长 同时绑定绑定设备数 累积绑定设备数 模块 许可版本 |
|  | 永久 | 可离线时长 同时绑定绑定设备数 累积绑定设备数 模块 许可版本 |
| 云锁 | 非永久 | 开始时间 结束时间 时间跨度 使用计数 模块 许可版本 |
|  | 永久 | 模块 许可版本 |

注意：修改其他许可信息，请重新发布许可

更新许可内容后，点击“确定”

![](https://developer.lm.virbox.com/course/images/course/cost---10.png "更新许可")

## 查看许可历史信息

1. 查看许可列表，选中许可列表右侧的许可历史信息按钮

2. 可查看该条许可的，所有历史操作记录

![](https://developer.lm.virbox.com/course/images/course/cost---4.png "查看许可历史信息")

3.点击“查看许可信息”，可查看每次操作许可的完整信息

4.点击“查看更新内容”，针对许可有更新操作的记录，可查看具体更新内容

![](https://developer.lm.virbox.com/course/images/course/cost--13.png "查看许可历史信息")

## 查看许可

查看许可分发列表，选中许可右侧的查看按钮，进入许可信息页面查看许可信息。

![](https://developer.lm.virbox.com/course/images/course/cost---5.png "查看许可")

## 删除许可

1. 查看许可列表，选中许可右侧的删除按钮。

2. 若许可仍在使用期内，删除许可后用户将不能再使用该许可对应的软件。

3. 点击"确定"，确认删除。

![](https://developer.lm.virbox.com/course/images/course/image082.png "删除许可")

## 批量删除许可

1. 查看许可列表，勾选列表左侧复选框选择需要删除的许可。

2. 若该许可已经发布给用户，删除后不会影响正常使用。

3. 点击“批量删除”，在弹出的对话框中需输入正确图片验证码。

4. 点击"确定"，确认删除。

![](https://developer.lm.virbox.com/course/images/course/delete-batch-license.png "批量删除许可")

## 许可解绑

1. 查看许可列表，许可形式为软锁的许可可查看该许可绑定机器的情况。

2. 点击"解绑"，在用户联网的情况下可将此条许从该机器删除，用户将不可使用与该许可对应的软件。若用户未联网则仍可使用，但一旦联网该许可会立刻删除。

![](https://developer.lm.virbox.com/course/images/course/image085.png "许可解绑")

## 许可筛选

1. 查看许可列表，点击筛选按钮，弹出筛选搜索框。

2. 选择产品和对应的模板，设置许可时间进行筛选

![](https://developer.lm.virbox.com/course/images/course/image088.png "许可筛选")
