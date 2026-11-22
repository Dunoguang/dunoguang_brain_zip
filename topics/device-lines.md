# 设备线与板级配置

| 设备 | 公开笔记 |
| --- | --- |
| DW99、VP19 | 同属 SL8541E 平台。面板、板级设备树和镜像布局分别核对。见 [DW99 内核](../areas/dw99-kernel.md) 与 [VP19 主线内核](../areas/vp19-kernel72.md)。 |
| 一加 AC3V | SM8650 平台。验证 GKI 与 vendor 模块复用时，检查显示驱动归属、模块 ABI 和容器所需配置。见 [AC3V 容器诊断](../areas/ac3v-conv.md)。 |
| Redmi 8A | MSM8937 平台。 [公开内核](https://github.com/Dunoguang/android_kernel_xiaomi_msm8937) |
| Redmi 9A | MT6765 平台。 [公开内核](https://github.com/Dunoguang/android_kernel_mt6765) |
| Redmi Note 11 Pro | pissarro。见 [内核构建笔记](../areas/pissarro-bakasu.md)。 |

测试镜像应记录设备树、内核配置、模块来源和目标分区。动态分区与 DSU 也需要在实际 ROM 上验证文件系统和挂载条件。接入硬件串口前，核对板端 IO 电压和适配器规格。
