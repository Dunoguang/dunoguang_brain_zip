# VP19 无屏启动排障

1. 先确定 Linux 启动的哪一段已经可观测。显示控制台依赖相关驱动探测，Android gadget 模式还依赖用户态配置。更早的停点可以用启动器已工作的通道或内核入口标记观察。
2. 保存一份只改设备树节点的对照镜像。保持相同的内核和 ramdisk，逐次启用 USB PHY、控制器或触控，记录最新阶段和主机上的枚举变化。
3. 从原始采集核对阶段标记，再解析堆栈。把标记的写入动作、主机收到字节的时刻以及是否发生重启分别记录。
4. 使用 ramoops 时，要验证目标复位确实保留对应 RAM，并核对同一份预留内存布局。

[公开诊断记录](https://github.com/Dunoguang/dw99_mainline_test/blob/upgrade-linux-7.3/Documentation/arch/arm64/dw99-porting-history.rst)
