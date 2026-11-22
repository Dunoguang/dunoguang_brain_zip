# VP19 U-Boot 移植验证

源码版 U-Boot 的调试分为启动进度、USB 可见性、实际内核交接、重启四类结果。使用屏幕或 USB 标记时，每次只调整一个停点，复测正式配置中的 USB 清理和正常重启。

引导 Linux 时，应把镜像格式、装载器计算的实际落点和最后的跳转入口一起核对。更换镜像后检查 `text_offset` 处理和缓存状态。出现黑屏时，结合 USB 枚举与复位表现判断程序进度。

[SL8541E U-Boot 源码与移植说明](https://github.com/Dunoguang/SL8541E-Uboot-Rebuild) · [U-Boot 构建专题](../topics/uboot-rebuild.md)
