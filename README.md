# 简单喵喵两句：

准备工作：

+ 准备一个至少 `8G` 及以上的 `USB 2.0` 或更高速率的 `U 盘`
  + **请确保这个 `U 盘` 格式为：`FAT32`**
  + 不能使用含有 `PE` 或 `DOC` 等其它引导盘
  + **注意：格式化 U 盘 操作会删除 U 盘里的所有数据，请务必备份数据**
+ 下载好要更新的 `BIOS` 文件
+ **警告⚠：**
  + **更新 `BIOS` 有风险，请慎重**
  + **更新 `BIOS` 程序执行期间，请勿打断更新或断电重启，否则导致主板不亮机（变砖）**
  + **本文档不为此负责！**

***

# `1.` 报错代码如下：

+ 可能你在更新铭瑄主板的新版 BIOS 时会遇到以下错误，如图所示：

```c
Error 189: File does not exist.
FPT Operation Failed.
```

![](https://github.com/wenyushu/MaxSun_Updating_BIOS_Error_189/blob/main/Iamge/189.png)

***

# `2.` 准备工作

## `1.` 查看系统信息（版本号）

+ 按组合键： `Win + R 键` ，输入 `msinfo32`，即可查看系统信息

```cmd
msinfo32
```

![](https://github.com/wenyushu/MaxSun_Updating_BIOS_Error_189/blob/main/Iamge/msinfo32.png)

+ 本文档演示主板为：`铭瑄 B760M 终结者 D5` 
+ 当前 BIOS 版本为：`E1.4D`，`2024/7/31` 更新

![E1.4D](https://github.com/wenyushu/MaxSun_Updating_BIOS_Error_189/blob/main/Iamge/E1.4D.png)

## `2.` 下载铭瑄官网最新的 BIOS 文件：

+ 版本为：`E1.5D` ，时间为：`08/12/2024`
+ 文件名：`MSTerminatorB760MD515.zip`

![](https://github.com/wenyushu/MaxSun_Updating_BIOS_Error_189/blob/main/Iamge/E1.5D.png)

### `2.1` 将 `EFI 文件` 夹拖入 U 盘根目录

+ 解压下载好的 `BIOS 更新文件压缩包` ，找到 `Shell Update BIOS` 目录下的 `EFI 文件夹`

![](https://github.com/wenyushu/MaxSun_Updating_BIOS_Error_189/blob/main/Iamge/Efi.png)

+ 将 `EFI 文件夹` 拖到 `U 盘根目录` 下，如图所示，但需注意：
  + 此 `U 盘` 不能是含有 `PE` 或 `其它引导` 的 `启动盘`
  + 请确保 `U 盘`  格式为 `FAT32`
  + 格式化 `U 盘` 会清空其内的数据，需做好备份
  + `EFI` 文件夹必须在 `U 盘` 根目录下，且不能含有其它文件

![U](https://github.com/wenyushu/MaxSun_Updating_BIOS_Error_189/blob/main/Iamge/U.png)

### `2.2` 编辑 `Startup.nsh` 文件

+ 选中 `Startup.nsh` 文件后，接着右键使用 `记事本` 或 `其它文本编辑器` 打开此文件，如图所示

![startup2](https://github.com/wenyushu/MaxSun_Updating_BIOS_Error_189/blob/main/Iamge/startup2.png)

+ 修改成如下图所示，接着保存即可

![startup3](https://github.com/wenyushu/MaxSun_Updating_BIOS_Error_189/blob/main/Iamge/startup3.png)

***

# `3.` 修改 BIOS 配置（禁用所有硬盘）

按照贴吧老哥 [蛋蛋 gnn](https://tieba.baidu.com/p/7884241319) 提供的解决方案中，有两种方法，如下所示：

|          方案 1          |         方案 2         |
| :----------------------: | :--------------------: |
| 关机断电后，拔掉所有硬盘 | 在 BIOS 中禁用所有硬盘 |
|   不推荐，这个太麻烦了   |         推荐√          |

## `1` 禁用所有硬盘（Nvme and Sata）

**由于本文档仅安装了三块 `NVMe` 的 `M.2 硬盘`， 因此，仅需在 `BIOS` 中找到：**

### `1.1` Nvme 部分

+  `Advanced` 选项 --->> `NVMe Configuration` 选项

![](https://github.com/wenyushu/MaxSun_Updating_BIOS_Error_189/blob/main/Iamge/NVMeConfiguration1.png)

+ 将这三块硬盘选项设置为 `禁用` ，即由 `Enabled` 设置为 `Disabled`，如图所示 

![](https://github.com/wenyushu/MaxSun_Updating_BIOS_Error_189/blob/main/Iamge/NVMeConfiguration2.png)

### `1.2` SATA 部分 

如果读者还安装了 `sata` 硬盘，则需要进入：

+ `Advanced` 选项 --->> `SATA Configuration` 选项
+ 将 `SATA` 硬盘选项由 `Enabled` 设置为 `Disabled`

![](https://github.com/wenyushu/MaxSun_Updating_BIOS_Error_189/blob/main/Iamge/SATA.png)

## `2.` 设置 `第一启动项` 为 `U 盘启动`

如下图所示

![](https://github.com/wenyushu/MaxSun_Updating_BIOS_Error_189/blob/main/Iamge/Boot.png)

## `3.` 等待跑码

![](https://github.com/wenyushu/MaxSun_Updating_BIOS_Error_189/blob/main/Iamge/FPT1.png)

## `4.` 跑码结束

如图所示，表示主板 `BIOS` 更新完成！

按电源键即可关机！

![](https://github.com/wenyushu/MaxSun_Updating_BIOS_Error_189/blob/main/Iamge/FPT2.png)

## `5.` 启用硬盘

读者需要再次按 `Del 键` 进入 `BIOS` ，将之前禁用的硬盘设置为启动即可~

## `6.` 查看版本 

更新后需要重新设置 PIN，读者自行设置即可。

如图所示，`BIOS 版本` 已更新至所需版本~

![BIOS](https://github.com/wenyushu/MaxSun_Updating_BIOS_Error_189/blob/main/Iamge/BIOS.png)

End~

***

# 鸣谢

感谢贴吧老哥 [蛋蛋 gnn](https://tieba.baidu.com/p/7884241319) 提供的解决方案，本文档仅在其方案上做了一点详细的说明和演示。


