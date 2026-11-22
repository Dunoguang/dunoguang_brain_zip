# DW99 内核与 vendor 适配

DW99 基于展锐 SL8541E。Watch-GKI 提供 4.4 厂商行为的对照，主线移植进度在 `dw99_mainline_test` 的 `upgrade-linux-7.3` 分支维护。 [Watch-GKI](https://github.com/Dunoguang/Watch-GKI) · [DW99 主线移植记录](https://github.com/Dunoguang/dw99_mainline_test/blob/upgrade-linux-7.3/Documentation/arch/arm64/dw99-porting-history.rst)

## Android 兼容

- HyperOS 4 的 `ApplicationSharedMemory` 使用 ashmem。恢复字符设备时也要保留 32 位 ioctl 和映射权限检查。
- `lmkd` 依赖 PSI。旧 vendor 使用 memcg v1 时，仍可挂载 cgroup v2 层级。测试应复现 ROM 的实际控制组布局。
- Mali GPU、蓝牙和 FM 依赖内核导出符号。启用 PSI 和 memcg v1 后应重新构建这三者，核对 `Module.symvers` 的导入 CRC，并用目标内核验证加载。
- EROFS 目录项提供独立长度；迁移 `iterate_dir()` 的回调时，同时核对返回值语义。WCN 应在重试时重新解析固件位置。

## 镜像与验证

这条线的 SPRD 镜像使用 gzip 内核、2048 字节页以及 SPRD 封装的 DTB。更换内核或 DTB 后应从最终镜像提取各段，核对大小、填充、配置与头部。需要与 ROM 组合时，vendor 里的模块应来自同一次内核构建。

7.3.5 调试版曾在 QEMU 验证 `lmkd` 启动、ashmem、控制组挂载、SIPC 映射和模块加载。eMMC、USB 枚举及其余板级外设需要实机确认。 [7.3.5 修复记录](https://github.com/Dunoguang/dw99_mainline_test/commit/75e8a57d9b01e7f8ffe02868dc8202fa93494197)
