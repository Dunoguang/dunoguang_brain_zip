# SL8541E 启动链

常见路径经过片上 Boot ROM、SPL、监控器、可信执行环境、U-Boot 和 Linux。各阶段需要独立核对封装头、载入位置、入口以及交接时的系统状态。

- 比较设备的镜像时，先区分封装头与实际 payload。记录解析起点，避免混用文件偏移和运行时地址。
- 用屏幕、串口或 USB 的阶段标记确认控制流。标记依赖当前阶段的驱动和定时器，应同时验证传输通道本身。
- 独立分析启动器、内核和用户态的设备树与镜像配置。即便使用同一款 SoC，也要按板级配置核对面板和外设。

[公开 U-Boot 构建仓库](https://github.com/Dunoguang/SL8541E-Uboot-Rebuild) · [VP19 U-Boot 验证](../areas/vp19-uboot-bringup.md)
