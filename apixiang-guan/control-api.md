# Control API

深思许可的管理接口，简称 ControlAPI 。主要提供加密锁信息的查询、许可内容和状态的查询、许可会话的查询等功能。

文件名 作用 说明

ss\_lm\_control.h ControlAPI 头文件 每个接口函数描述

slm\_control\_api.lib ControlAPI 的静态库 接口的实现

slm\_control.dll ControlAPI 的动态库 接口的实现

| 文件名 | 作用 | 说明 |
| :--- | :--- | :--- |
| ss\_lm\_control.h | ControlAPI 头文件 | 每个接口函数描述 |
| slm\_control\_api.lib | ControlAPI 的静态库 | 接口的实现 |
| slm\_control.dll | ControlAPI 的动态库 | 接口的实现 |

下面是一段 C 语言调用 ControlAPI 的示例：

```c
//  本示例简单展示如何获取加密锁内许可信息
#include <stdio.h>
#include "json/json.h" //  示例中采用 jsoncpp 解析 json 结构
#include "ss_error.h"
#include "ss_lm_control.h"
int main(int argc, char **argv)
{
SS_UINT32 buf_size = 0;
SS_UINT32 ret = 0;
void *ipc = NULL;
char *dev_desc = NULL;
Json::Reader reader;
Json::Value root;
Json::Value desc;
ret = slm_client_open(&ipc);
if (ret != SS_OK)
{
return -1;
}
printf("slm_client_open ok\n");
ret = slm_get_all_description(ipc, JSON, &dev_desc);
if (ret != SS_OK)
{
printf("slm_get_all_description failed,errorcode=0x%08x",ret);
}
else
{
printf("slm_get_all_description ok\n");
printf("begin prase all lock\n");
if (!reader.parse(dev_desc, root))
{
printf("parse error \n");
}
else
{
printf("parse ok \n");
}
}
std::string dev_type;
std::string host_name;
std::string ip;
std::string sn;
std::string devp_id;
std::string print_str;
int dev_num = root.size(); //  设备数量
for (int i = 0; i < dev_num; ++i)
{
desc = root[i];
if(desc != NULL)
{
char *lic_context = NULL;
print_str = "\nbegin to read license \n";
if (!desc["host_name"].isNull())
{
host_name = desc["host_name"].asString();
print_str += "[host_name:" + host_name + "] ";
}
if (!desc["ip"].isNull())
{
ip = desc["ip"].asString();
print_str += "[ip:" + ip + "] ";
}
if (!desc["type"].isNull())
{
dev_type = desc["type"].asString();
print_str += "[type:" + dev_type + "] ";
}
if (!desc["sn"].isNull())
{
sn = desc["sn"].asString();
print_str += "[sn:" + sn + "] ";
}
if (!desc["developer_id"].isNull())
{
devp_id = desc["developer_id"].asString();
print_str += "[devp_id:" + devp_id + "] ";
}
print_str += "\n";
printf(print_str.c_str());
ret = slm_read_brief_license_context(ipc, JSON, desc.toStyledString().c_str(), &lic_context);
if(ret == SS_OK && lic_context != NULL)
{
printf(lic_context);
printf("\n");
slm_free(lic_context);
lic_context = NULL;
printf("slm_read_brief_license_context ok\n");
}
else
{
printf("slm_read_brief_license_context failed, [sn=%s] \n[errorcode=0x%08x]", sn.c_str(), ret);
}
}
}
slm_client_close(ipc);
return 0;
```





