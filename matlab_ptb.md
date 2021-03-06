# PsychToolbox 安装和运行指南

> 更新时间 2020年2月13日

## 0. MATLAB 软件安装指南

Psychtoolbox 心理学实验工具箱（下称 PTB），是 MATLAB 的一组代码库，其用于在 MATLAB 环境下调用 OpenGL 完成视觉等刺激的展示以及键盘、语音、鼠标等输入的记录。PTB 依赖于 MATLAB 软件，推荐安装使用 2018 之后的 MATLAB 版本，具有较高的速度和稳定性。MATLAB 的安装参见：[CSDN](https://blog.csdn.net/COCO56/article/details/96425259)

## 1. PTB 包安装指南

最简单的方法，下载 PTB 最新版本，解压到一个安全稳定的位置，然后找到 Psychtoolbox > SetupPsychtoolbox.m 文件，将其拖拽到 MATLAB 的命令行中，一路 ENTER 即可安装。

> 存在问题（截至2019年11月30日）:
> PTB 尚不支持 macOS Catalina（2019年11月30日）。
> PTB 已知在 Windows 10 1909 版本中无法直接运行 —— 缺少 OpenGL 的 gstreamer 组件，见后文下载地址。

## 2. 相关下载链接

### 2.1 MATLAB

- MATLAB 2018b Windows 版本下载

> || 上述文件点此链接下载：[百度网盘](https://pan.baidu.com/s/1Pl64M42QHU78DbpobQpXPQ) || 访问密码：`d8jt` || 失效不补

> 备注：MATLAB 2019b 开始，允许按照软件包购买 MATLAB，其基本程序只需 29 美元，此外，提供大部分功能包的学生版本，价格约 55 美元 [官方购买地址](https://ww2.mathworks.cn/store/link/products/student/ML)。因此，不提供任何破解程序。

> 备注：MATLAB 2018a、2018b 之后版本大幅度提高了程序响应速度、内置了 Java 8 虚拟机、使用了 JxBrowser 浏览器核心组件，且对 git 和单元测试提供支持，提供较好的字符串支持，可用性较好，且容易利用 JVM Java 生态众多的类库以及先进的开发理念，以及 Python 生态数据展示、分析的能力，推荐使用 2018、2019 版本。

> 备注：有文章（不做任何保证）提供了一个安装和激活上述 MATLAB 的方法：[点此查看](https://blog.csdn.net/COCO56/article/details/96425259)

### 2.2 Psychtoolbox

- PTB 3.0.16 - MATLAB 包

- Gstreamer - MSVC Windows 版本

- MRC(2018b) Windows 版本 - InstallAgent

> || 上述文件点此链接下载：[SharePoint](http://go.mazhangjing.com/ccnupalshareptb) || 访问密码：`ccnupal` || [失效联系](mailto://matlab@mazhangjing.com)

### 2.3 Software Development Tools

- Jdk-8u211-windows-x64 JVM 开发工具套件
- Visual Studio Code 编辑器
- Git 2.15.1.2 代码协作工具
- Notepad++ 7.8.2 编辑器
- Dr.Racket Lisp 解释器
- IDEA 2019.3.2 集成开发环境 IDE
- Scala IDEA 插件 2019.3.2

> || 上述文件点此链接下载：[SharePoint](http://go.mazhangjing.com/ccnupalsharecode) || 访问密码： `ccnupal` || [失效联系](mailto://matlab@mazhangjing.com)

> Scala sbt 包管理工具、Java Maven 包管理工具国内镜像：[华为云](https://mirrors.huaweicloud.com)、[阿里云(仅有 Maven 仓库)](https://aliyun.com)


## 3. 开发环境配置指南（高级）

MATLAB 是矩阵实验室的简称，也是一套基于数值计算的科研实验平台，其采用 MATLAB 同名动态语言进行项目的描述和编写，包含大量开箱即用的工具箱、函数，支持工作区，可以快速查看当前变量，快速作图以及统计分析。函数大部分使用 C/C++ 封装，GUI 界面采用 Java 编写。其和 C、C++、Java、Python、.NET 的交互支持（互相调用）支持完善。得益于内置的 Java 虚拟机，MATLAB 开箱即用的支持跨平台集成 JVM 生态数以千万计的类库的可能性。MATLAB 语言基于脚本，但对 OOP 也提供支持，其开发灵活，REPL 及历史记录功能好用，mlint 语法分析做的也不错，但是语法特性、编辑器、以及代码结构管理、包机制、包管理器支持较差，因此考虑使用 Code 代替默认的文本编辑器。

MATLAB 自带的编辑器提供了代码分析 mlint，不过在代码补全、智能完成、快捷操作上尚且不及 VSCode。因此，本文使用一些 VSCode 插件配置 MATLAB，在编写脚本、REPL 执行命令时都非常好用：

### 3.1 获取 MATLAB 和 MLINT 路径

获取 MATLAB 安装文件夹的 matlab 程序路径以及 mlint 代码检查程序路径

matlab 程序路径位于 `bin/` 文件夹下

- macOS：比如 `/Volumes/Apps/MATLAB.app/bin/matlab`，macOS 需要在安装文件右键 - 显示包内容以显示真实文件夹。
- Windows：比如 `C:\\Program Files\\MATLAB\\R2018b\\bin\\matlab.exe`，注意，使用双反斜线替代单反斜线。

mlint 程序路径位于 `bin/[win64,maci64,...]/` 文件夹下

- macOS：比如 `/Volumes/Apps/MATLAB.app/bin/maci64/mlint`，macOS 需要在安装文件右键 - 显示包内容以显示真实文件夹。
- Windows：比如 `C:\\Program Files\\MATLAB\\R2018b\\bin\\win64\\mlint.exe`，注意，使用双反斜线替代单反斜线。

### 3.2 安装 Visual Studio Code 及插件

下载并安装 VSCode：[微软 Visual Studio Code 官方下载](https://code.visualstudio.com/)

打开 VSCode，在左侧扩展选项卡中，分别搜索 `code runner`、`matlab` 安装扩展 `Code Runner by Jun Han` 和 `Matlab by Xavier Hahn`，点击安装。

首先配置 Matlab 插件，打开菜单 - 偏好 - 设置，搜索 `matlab`，设置 Linter Encoding为 GBK，填写 Matlabpath 和 Mlintpath 路径，下图为 macOS 的示例，Windows 在此处需要使用双反斜杠 `\\` 而不是 `/`，填写自己安装的 MATLAB 位置即可。

![](http://static2.mazhangjing.com/20191202/53531b7_matlab_vscode_1.png)

之后，通过搜索 `auto save` 和 `guess` 来设置 Code 的自动保存 `Files: Auto Save` 为 autoDelay，以及自动猜测编码 `Files: Auto Guess Encoding`，这样可以提高 mlint 提示的速度并且避免手动更换文件编码。

本质上，启用如下配置：

```json
"matlab.matlabpath": "/Volumes/Apps/MATLAB.app"
"matlab.linterEncoding": "GBK"
"matlab.mlintpath": "/Volumes/Apps/MATLAB.app/bin/maci64/mlint"
"files.autoSave": "afterDelay"
"files.autoGuessEncoding": true
```

> 注意，替换 matlabpath 和 mlintpath 为你自己的地址，如果使用上图所示的图形界面配置，则不需要重复设置此 JSON 配置。

之后配置 Code Runner 插件，按照如下配置即可，这样做之后可以通过点击右上角的运行三角按钮来执行脚本，不过，每次执行都会创建一个新的 MATLAB 实例，非常耗时，因此，仅做备用。在搜索框直接复制 `files.associations`，点击编辑 settings.json，然后粘贴如下代码：

```json
"files.associations": {
	"*.m": "matlab"
},
"code-runner.executorMap": {
	"matlab": "cd $dir && /Volumes/Apps/MATLAB.app/bin/matlab -nosplash -nodesktop -nodisplay -r $fileNameWithoutExt" 
}
```

> 注意，替换 `code-runner.executorMap` 中的 `/Volumes/Apps/MATLAB.app/bin/matlab` 为你自己的 matlab 路径，注意检查代码之前和之后注意检查是否有遗失的逗号。

### 3.3 配置 PATH

之后配置 PATH：

#### 3.3.1 macOS

在 macOS 下，修改 `~/.bash_profile` 文件，添加如下指令：

```bash
export PATH=/Volumes/Apps/MATLAB.app/bin:$PATH
alias matlabshell="matlab -nodisplay -nosplash -nodesktop"
alias matlabgui="matlab -nosplash -nodesktop"
```

之后 `source ~/.bash_profile`，使其生效。这样之后，就可以在命令行执行 matlabshell 创建无窗口 REPL，以及 matlabgui 创建不带开始屏幕的 MATLAB 实例了。

#### 3.3.2 Windows

依次打开 Windows 资源管理器 > 此电脑（右键） > 属性 > 高级系统设置 > 环境变量 > 系统变量中的 Path 条目 > 新建 > 输入 matlab 路径，注意，使用单反斜杠，且到 bin 目录为止，比如：`C:\Program Files\MATLAB\R2018b\bin` > 将其移动到较高优先级 > 确定。如下图所示：

![](http://static2.mazhangjing.com/20191205/8360cc9_path_windows.png)

这样就可以在任意终端执行 `matlab` 来启动 matlab 实例了。

### 3.4 使用 Code 替代 MATLAB IDE

当打开一个文件夹后，我们就可以使用 Code 的编辑器编辑代码，使用 mlint 自动检查语法错误，然后在 Code 中通过内置的命令行来执行 REPL 查看工作区状态，以及在此 MATLAB 实例中执行代码了，如下图所示：

![](http://static2.mazhangjing.com/20191202/082fa7b_vscode_matlab_demo.png)

## 4. 联系方式

> 联系地址：issure@mazhangjing.com