# U-Boot 引导 GKI 镜像时的布局检查

Android boot image 的头部随版本演进。对旧 U-Boot 增加 GKI 支持时，先识别实际头版本，再按版本处理页对齐、字段偏移、压缩内核与各分区。 [AOSP boot image 头](https://source.android.com/docs/core/architecture/bootloader/boot-image-header)

使用较新的 GKI 格式时，检查 `boot` 与 `vendor_boot` 各自提供的内核、ramdisk 和 DTB。单独核对装载器的分区读取和解析、内核的板级驱动集、vendor ramdisk 的挂载条件。 [AOSP vendor_boot](https://source.android.com/docs/core/architecture/partitions/vendor-boot-partitions)
