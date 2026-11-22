# U-Boot USB 实时日志

uboot-usblog 提供启动器 USB 日志采集。读端要确认接口已有效占用，维持挂起的读取请求，并按端点的最大传输大小分块处理。连续超时、端口消失和重连应记录为不同事件。 [uboot-usblog](https://github.com/Dunoguang/uboot-usblog)

以启动标记为采集边界，每次启动新建文件。原始字节宜保留供离线解码。USB PHY 和中断由 Linux 接管后，启动器的发送轮询不再参与，定位问题时需结合内核阶段与主机枚举记录。 [VP19 无屏启动排障](../areas/vp19-kernel-debug.md)
