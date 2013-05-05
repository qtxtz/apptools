Android多渠道打包工具
========

1. 环境设置保证apktool运行正常
========
可参考官方项目：https://code.google.com/p/android-apktool/

2.打包流程
========
1.设置当前process 的环境变量，保证 apktool 可以正常工作<br />
2.执行 apktool d --no-src -f xxxx.apk temp 拆解apk<br />
3.替换 AndroidManifest.xml 中的 channelFlag字符为指定渠道<br />
4.执行 apktool b temp unsigned.apk 重新打包apk<br />
5.执行 jarsigner 生成签名后的 apk 文件<br />
6.执行 zipAlign 生成对齐优化后的 apk 文件<br />
7.回到 3 替换新的渠道<br />
8.完成打包<br />

3.注意事项
========
1.如果您的电脑以前使用过apktool工具请删除工具生成老的framework.jar 路径:
c:\Documents and Settings\%current user%\apktool\framework\*

2.请保证java与android环境变量不存在空格，如有请在代码执行命令前直接写上路径后运行比如：
D:\android-sdk-windows\tools\zipalign

3.不支持Java jar包中包含有资源文件的apk项目，受apktool工具本身功能限制
