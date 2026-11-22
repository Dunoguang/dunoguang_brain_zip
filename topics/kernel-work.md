# 内核移植检查项

## 构建和配置

- Watch-GKI 用于对照 DW99 的厂商内核。主线工作树包含板级驱动和新的内核 API，适配时先用原厂行为建立测试预期。 [Watch-GKI](https://github.com/Dunoguang/Watch-GKI) · [主线内核](https://github.com/Dunoguang/dw99_mainline_test)
- 更新版本后检查 hrtimer 初始化、VFS 的 idmapped mount 参数、bio 构造、conntrack、dentry 索引、inode 时间戳访问器和 Kconfig 依赖。
- 检查生成的 `.config`。缓存构建前重新生成配置，再核对旧选项是否换名或被依赖强制选择。编译外部模块时使用目标内核的输出目录与 `Module.symvers`。
- 集成 KernelSU 或 SuSFS 时，核对实际编译进树的版本、钩子和 Kconfig。出现未解析符号时，从构建日志追踪实际源码来源和依赖，再进行功能验证。 [SuSFS 移植仓库](https://github.com/Dunoguang/susfs4oki)

## 运行时验证

狭窄的单变量对照适合定位启动故障。提交前分别核对目标配置、DTB、相关模块、用户态接口和镜像各段。对涉及板级时序的改动，实机日志是最终依据。

[DW99 启动与适配记录](https://github.com/Dunoguang/dw99_mainline_test/blob/upgrade-linux-7.3/Documentation/arch/arm64/dw99-porting-history.rst)
