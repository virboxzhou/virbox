# Runtime API

深思许可的使用接口，简称 RuntimeAPI ，深思许可体系最为关键的接口，开发者软件通过此接口进行许可的访问，即开发商软件直接使用到的接口。

SDK 中的文件体现

| 文件名 | 作用 | 说明 |
| :--- | :--- | :--- |
| ss\_lm\_runtime.h | RuntimeAPI 头文件 | 每个接口函数描述 |
| slm\_runtime\_api.lib | RuntimeAPI 的静态库 | 含反调试功能，开发者软件正式发布时选用 |
| slm\_runtime\_api\_dev.lib | RuntimeAPI 的开发静态库 | 不含反调试功能，开发者开发过程中可使用的库 |
| slm\_runtime.dl | RuntimeAPI 的动态库 | 含反调试功能，开发者软件正式发布时选用 |
| slm\_runtime\_dev.dll | RuntimeAPI 的开发动态库 | 不含反调试功能，开发者开发过程中可使用的库 |
| slm\_runtime\_easy.dll | RuntimeAPI 的动态库 | 简易接口，方便其他语言调用 |
| slm\_runtime\_easy\_dev.dll | RuntimeAPI 的开发动态库 | 简易接口，方便其他语言调用 |

注：开发库（带 dev 字样）不具有反调试功能，是方便开发者在开发过程中调试软件使用的，不可在发布时使用，否则软件不具备反

调试功能，降低了黑客的破解难度；开发过程中请使用调试库 \(\_dev\) ，否则使用编译器调试代码过程中会出现程序异常退出的情况。

下面是一段 C 语言调用 RuntimeAPI 的示例：

```
#include "stdio.h"
#include "ss_lm_runtime.h"
int main(int argc, char **argv)
{
SLM_HANDLE_INDEX hslm = 0;
BYTE original_data[TEST_ENCRYPT_DATA_SIZE ] = {"test_data1234567890"};
BYTE encrypted_data[TEST_ENCRYPT_DATA_SIZE] = {0};
BYTE decrypted_data[TEST_ENCRYPT_DATA_SIZE] = {0};
SS_UINT32 sts = SS_OK;
SS_BYTE psd[16] = { 0xDB, 0x3B, 0x83, 0x8B, 0x2E, 0x4F, 0x08, 0xF5, 0xC9, 0xEF, 0xCD, 0x1A, 0x5D, 0xD1, 0x63, 0x41 }; //  开发者 API 密码，每个开发者独立，必须也只能从深思开发者中心获取到。
ST_LOGIN_PARAM login_struct = {0};
ST_INIT_PARAM st_init_param = {0};
//0.  全局初始化函数，调用此方法来初始化 slm_runtime
st_init_param.version = SLM_CALLBACK_VERSION02;
st_init_param.pfn = &(app_ss_msg_core);
memcpy(st_init_param.password, psd, sizeof(psd));
sts = slm_init(&(st_init_param));
//1. slm_login  登录许可
login_struct.license_id = 0; // 登录 0 号许可
login_struct.size = sizeof(ST_LOGIN_PARAM);
login_struct.timeout = 86400;
sts = slm_login(login_struct,STRUCT, &(hslm),NULL);//
if (SS_OK == sts)
{
printf("slm_login ok, 许可登录成功！ \n");
}
else
{
printf("slm_login faield error = 0x%08X,  许可登录失败： %s\n",sts, slm_error_msg(sts, 1));
goto end;
}
// 2.  使用许可加密对测试数据进行加密
printf("before encrypt: %s\n", original_data);
sts = slm_encrypt(hslm, original_data, encrypted_data, TEST_ENCRYPT_DATA_SIZE);
if (SS_OK == sts)
{
printf("slm_encrypt ok ！许可加密成功 \n");
//hex printf encrypted_data ，可通过十六进制打印，查看加密后的数据是不可读的
}
else
{
printf("slm_encrypt faield error = 0x%08X,  加密失败 : %s\n",sts, slm_error_msg(sts, 1));
goto end;
}
// 3.  使用许可解密对加密后的数据进行解密
sts = slm_decrypt(hslm, encrypted_data, decrypted_data, TEST_ENCRYPT_DATA_SIZE);
if (SS_OK == sts)
{
printf("slm_decrypt ok ！许可解密成功 \n");
//  在此对比原始数据 original_data  和解密后数据 decrypted_data 是否一致
}
else
{
printf("slm_decrypt faield error = 0x%08X,  解密失败 : %s\n",sts, slm_error_msg(sts, 1));
goto end;
}
end:
slm_logout(hslm);
return sts;
```



