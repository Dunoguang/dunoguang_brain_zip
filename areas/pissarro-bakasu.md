# Redmi Note 11 Pro 内核构建

pissarro 的一轮移植集成了 BakaSU 和 SuSFS 2.3.0。验收涵盖实际编译配置、预期功能和最终镜像。符号存在只能证明接口被链接，需要继续检查调用路径与功能行为。

- 用最终生成的 `.config` 检查 Kconfig 的 `select` 是否改变了 defconfig 意图。
- AnyKernel3 打包应核对目标设备代号、`Image` 的压缩格式以及 DTB 的来源与拼接方式。
- 内核与 vendor 模块应核对导出符号版本、设备树和实际加载结果。

[公开内核仓库](https://github.com/Dunoguang/android_kernel_xiaomi_pissarro) · [AnyKernel3](https://github.com/osm0sis/AnyKernel3)
