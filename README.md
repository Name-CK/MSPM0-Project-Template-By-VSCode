## 一、软件安装
**注意：所有软件的安装目录均不用出现中文和空格。**
1. 编辑器：VSCode https://code.visualstudio.com
	内部插件
	1. 项目管理：Embedded IDE（EIDE）
	2. 调试：Cortex-Debug
	3. 语法：C/C++
2. 编译器：GNU Arm Embedded Toolchain https://developer.arm.com/downloads/-/gnu-rm
3. 调试（&烧录）器：OpenOCD（这里使用xPack OpenOCD，免去自己编译的过程） https://xpack-dev-tools.github.io/openocd-xpack/docs/releases
4. 芯片SDK：MSPM0-SDK https://www.ti.com.cn/product/cn/MSPM0G3507?keyMatch=mspm0g3507&tisearch=universal_search#software-development
5. 芯片配置工具：SYSCONFIG https://www.ti.com.cn/tool/cn/SYSCONFIG?keyMatch=SYSConfig&tisearch=universal_search
6. 项目模版： https://github.com/Name-CK/MSPM0-Project-Template-By-VSCode

### 其它非必要软件
1. VSCode插件：切换语言为中文 -> Chinese (Simplified) (简体中文)
2. VSCode插件：AI辅助编程 -> Lingma - Alibaba Cloud AI Coding Assistant（通义灵码）; GitHub Copilot Chat等，选择一款即可
3. TI官方烧录工具：UNIFLASH 软件编程工具 -> https://www.ti.com.cn/tool/cn/UNIFLASH


## 二、环境配置
### 1.添加TI工具环境变量
右键 此电脑 -> 属性 -> 高级系统设置 -> 环境变量 -> XXX的用户变量 中 新建：
变量名：TIMSPM0_TOOLBOX
变量值：D:\Tool\TI\mspm0_sdk_2_05_00_05;D:\Tool\TI\sysconfig_1.26.3
填写完成后连续三次点击 确定 ，退回到"此电脑 -> 属性 "界面即可。

其中，**变量值**<u>依次</u>**为<u>m0sdk目录</u>和<u>sysconfig目录</u>中间使用分号';'隔开**。

### 2.在VSCode-EIDE中配置相关工具链地址
打开VSCode -> 上面菜单栏 File(文件) -> 首选项 -> 设置。
搜索以下选项并按其要求配置：
- EIDE.ARM.GCC: Install Directory
- EIDE.Open OCD: Exe Path


## 三、打开项目模版并编译

1.第一次启动项目-创建SDK软连接
打开 **Launcher.exe** 点击 创建/修改SDK软连接 。操作成功会有弹窗提醒。
若操作失败则依据弹窗内容进行操作，如 以管理员身份启动 ，添加环境变量。
注：重建SDK软连接后，可能需要重启VSCode才能识别到相关文件。

2.在 Launcher.exe 点击 使用EIDE打开项目,等待VSCode加载完毕，下方状态栏有Build和Flash按钮，提供构建（编译）和 烧录 功能。
可在左侧边栏EIDE栏目中找到 烧录配置 ，可以进行调试器的切换。
注：若 Launcher.exe 中按钮为禁用状态，则是 环境变量配置 问题。

3.若需打包项目，先使用 Launcher.exe 删除 SDK软连接，否则会将SDK一起打包，使用Git进行版本控制是同理，需要忽略 IDE\EIDE\MSPM0_SDK 目录。

4.需要更换芯片型号直接使用SysConfig创建对于的配置文件即可。
