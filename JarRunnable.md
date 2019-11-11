# .jar 文件运行说明

.jar 是 Java 平台可执行二进制程序的扩展名，需要 Java 平台的支持方可执行。

## Java 平台下载

Java 平台有多个不同的实现方式，比如 IBM 的 OpenJ9, Oracle 的 Hotspot, OpenJDK 委员会的 OpenJDK，以及根据 OpenJDK 变种的，比如 Alibaba 的 DragonWell，此外，还包括一些其余发行商实现的其它 Java 标准，比如 Amazon 和 Apple。

Java 实现的版本目前常用的有 14, 6, 7, 8, 9, 10, 11, 12, 13。其中 版本 8 包含较为成熟的 JavaFx GUI 框架，并且引入了函数式编程语法，在实际生产中应用较广。

Java 版本分为 JDK 和 JRE，前者称之为开发环境，后者称之为运行时，后者仅提供可供运行的最小文件体积。对于需要在命令行执行 java 命令来运行 Java 程序，需要 JDK(Java Development Kit)，而不仅仅是 JRE(Java Runtime)

由于官方的标准 Java 平台的实现时 Oracle 的 Hotspot，因此下面提供了其下载地址：

### Windows

JDK8: http://static2.mazhangjing.com/java/jdk-8u211-windows-x64.exe

JRE8: http://static2.mazhangjing.com/java/jre-8u211-windows-x64.exe

### macOS

JDK8: http://static2.mazhangjing.com/java/jdk-8u211-macosx-x64.dmg

JRE8: http://static2.mazhangjing.com/java/jre-8u211-macosx-x64.dmg

## 运行说明

当安装好 Java 平台后，一般情况下，可以直接双击 jar 文件执行其代码。

也可以通过在命令行运行 `java -jar xxx.jar` 来查看其执行的输出结果，更详细的了解其执行过程。