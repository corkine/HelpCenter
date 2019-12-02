# PsychToolbox 安装和运行指南

> 更新时间 2019-12-02

## PTB 包安装指南

最简单的方法，下载 PTB 最新版本，解压到一个安全稳定的位置，然后找到 Psychtoolbox > SetupPsychtoolbox.m 文件，将其拖拽到 MATLAB 的命令行中，一路 ENTER 即可安装。

### 存在问题（截至2019年11月30日）

PTB 尚不支持 macOS Catalina（2019年11月30日）。
PTB 已知在 Windows 10 1909 版本中无法直接运行 —— 缺少 OpenGL 的 gstreamer 组件，见后文下载地址。

## 开发环境配置指南

MATLAB 自带的编辑器提供了代码分析 mlint，不过在代码补全、智能完成、快捷操作上尚且不及 VSCode。因此，本文使用一些 VSCode 插件配置 MATLAB，在编写脚本、REPL 执行命令时都非常好用：

### 获取 MATLAB 和 MLINT 路径

获取 MATLAB 安装文件夹的 matlab 程序路径以及 mlint 代码检查程序路径

matlab 程序路径位于 `bin/` 文件夹下，比如 `/Volumes/Apps/MATLAB.app/bin/matlab`，macOS 需要在安装文件右键 - 显示包内容以显示真实文件夹。

mlint 程序路径位于 `bin/[win64,maci64,...]/` 文件夹下，比如 `/Volumes/Apps/MATLAB.app/bin/maci64/mlint`。

### 安装 Visual Studio Code 及插件

下载并安装 VSCode：[微软 Visual Studio Code 官方下载](https://code.visualstudio.com/)

打开 VSCode，在左侧扩展选项卡中，分别搜索 `code runner`、`matlab` 安装扩展 `Code Runner by Jun Han` 和 `Matlab by Xavier Hahn`。

首先配置 Matlab 插件，打开菜单 - 偏好 - 设置，然后找到 Extensions - Matlab Configure，填写 matlab 和 mlint 路径，设置编码为 GBK：

![](http://static2.mazhangjing.com/20191202/53531b7_matlab_vscode_1.png)

之后，设置 Code 的自动保存，以及自动猜测编码，这样可以提高 mlint 提示的速度并且避免手动更换文件编码。

> 可以直接将相应设置项，比如 `files.autoGuess..`，将其复制到搜索框，即可查看和修改。

本质上，启用如下配置：

```json
"matlab.matlabpath": "/Volumes/Apps/MATLAB.app"
"matlab.linterEncoding": "GBK"
"matlab.mlintpath": "/Volumes/Apps/MATLAB.app/bin/maci64/mlint"
"files.autoSave": "afterDelay"
"files.autoGuessEncoding": true
```

之后配置 Code Runner 插件，按照如下配置即可，这样做之后可以通过点击右上角的运行三角按钮来执行脚本，不过，每次执行都会创建一个新的 MATLAB 实例，非常耗时，因此，仅做备用。

```json
"files.associations": {
	"*.m": "matlab"
}
"code-runner.executorMap" {
	"matlab": "cd $dir && /Volumes/Apps/MATLAB.app/bin/matlab -nosplash -nodesktop -nodisplay -r $fileNameWithoutExt" 
}
```

### 配置 PATH

之后配置 PATH，在 macOS 下，修改 ~/.bash_profile 文件，添加如下指令：

```bash
export PATH=/Volumes/Apps/MATLAB.app/bin:$PATH
alias matlabshell="matlab -nodisplay -nosplash -nodesktop"
alias matlabgui="matlab -nosplash -nodesktop"
```

之后 `source ~/.bash_profile`，使其生效。这样之后，就可以在命令行执行 matlabshell 创建无窗口 REPL，以及 matlabgui 创建不带开始屏幕的 MATLAB 实例了。

### 使用 Code 替代 MATLAB IDE

当打开一个文件夹后，我们就可以使用 Code 的编辑器编辑代码，使用 mlint 自动检查语法错误，然后在 Code 中通过内置的命令行来执行 REPL 查看工作区状态，以及在此 MATLAB 实例中执行代码了，如下图所示：

![](http://static2.mazhangjing.com/20191202/082fa7b_vscode_matlab_demo.png)

# 相关下载链接

## PTB 3.0.16

> OSS 带宽费用高昂，请勿多次或恶意下载、分享

http://go.mazhangjing.com/ptb_last

## Gstreamer - MSVC Windows 版本

> OSS 带宽费用高昂，请勿多次或恶意下载、分享

http://go.mazhangjing.com/gstreamer_msvc

## MRC(2018b) Windows 版本

> OSS 带宽费用高昂，请勿多次或恶意下载、分享

http://go.mazhangjing.com/mrc2018b_win

## MATLAB 2018b Windows 版本下载

https://pan.baidu.com/s/1Pl64M42QHU78DbpobQpXPQ 提取码: d8jt

> 备注：MATLAB 2019b 开始，允许按照软件包购买 MATLAB，其基本程序只需 29 美元，此外，提供大部分功能包的学生版本，价格约 55 美元 [官方购买地址](https://ww2.mathworks.cn/store/link/products/student/ML)。因此，不提供任何破解程序。

> 备注：MATLAB 2018a、2018b 之后版本大幅度提高了程序响应速度、内置了 Java 8 虚拟机、使用了 JxBrowser 浏览器核心组件，且对 git 和单元测试提供支持，提供较好的字符串支持，基本赶上了 10 年前的二流语言（eg. Python） 的软件开发水平，可用性较好，且容易利用 JVM Java 生态众多的类库以及先进的开发理念，以及 Python 生态数据展示、分析的能力，推荐使用 2018、2019 版本。

## Python 3.6.8 Windows 版本下载

> 适用于 MATLAB 2018b 配套执行环境

> OSS 带宽费用高昂，请勿多次或恶意下载、分享

http://go.mazhangjing.com/python368

## Scala 2.12.6 Jar 文件

> OSS 带宽费用高昂，请勿多次或恶意下载、分享

https://mvnrepository.com/artifact/org.scala-lang/scala-library/2.12.6

http://go.mazhangjing.com/scala2126

# 联系方式

> 联系地址：matlab_issure@mazhangjing.com