# VP19 主线内核移植笔记

VP19 的启动排障从 7.2 移植树延伸到 7.3。用编译配置、设备树和实机日志建立每轮基线，随后缩小停点并用公开源码验证修复。 [DW99 主线移植记录](https://github.com/Dunoguang/dw99_mainline_test/blob/upgrade-linux-7.3/Documentation/arch/arm64/dw99-porting-history.rst)

## 早期内存映射

两处早期初始化写入曾落在只读映射里。`kimage_voffset` 在早期表切换后继续写入，`vmlinux_build_id` 在解析 build ID 时由 `memcpy()` 填充。定位时应把符号地址、ELF 段、页表属性和实际写入时机放在一起检查。只看到 `memcpy()` 附近停住无法判断是源指针还是目的页权限。

修复后重新核对 `Image`、`System.map` 和测试点。编译一轮就替换这三个输入，避免拿另一轮的符号表解释当前日志。对压缩镜像先取出内核，再读取 ELF 对应的配置和符号。

## 定时器与 USB

- DT 的 Arm PPI 描述必须明确各路中断。时钟计数在变而定时睡眠没有唤醒时，应同时检查架构定时器选路和独立广播时钟事件源。
- 启动器提供的 USB 早期控制台依赖启动器的寄存器状态、中断与发送轮询。Linux USB PHY 接管是一个独立可测的边界。持续记录主机端口状态和内核阶段，便于判断是通道停止还是系统停止。
- 把早期入口、切页表、异常处理和进入 `start_kernel()` 当作独立观察点。只在基线固定后记录新增标记对控制流的影响。

## 7.3.5 接续

后续测试进入了 Android 用户态。把 eMMC 超时、应用共享内存、WCN 固件、基带共享内存、按键与充电分开取证，最后合进同一次源码更新。现有测试证明了若干通用 ABI 和文件路径行为，板级时序仍依赖 VP19 实测。 [兼容修复](https://github.com/Dunoguang/dw99_mainline_test/commit/75e8a57d9b01e7f8ffe02868dc8202fa93494197)
