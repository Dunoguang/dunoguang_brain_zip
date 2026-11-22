# SL8541E U-Boot 构建

VP19 移植线基于 U-Boot 2015.07。板级编译目标、设备树、工具版本和封装过程见公开仓库。现代 GCC 和 DTC 构建旧代码时，重点检查生成头文件、libfdt API 和 C 语言模式。 [SL8541E-Uboot-Rebuild](https://github.com/Dunoguang/SL8541E-Uboot-Rebuild)

更换面板时，核对识别序列、复位顺序、模式和时序。在 U-Boot 与内核交接前验证实际加载地址、镜像入口及必要的收尾操作，同时测试冷启动与软件重启。 [VP19 移植验证](../areas/vp19-uboot-bringup.md)
