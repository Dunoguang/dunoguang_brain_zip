# 浏览器内的固件镜像处理

SPRD-Uboot-Patcher 的网页界面在浏览器中读取并处理用户选择的文件。项目提供中文、英语和葡萄牙语界面。 [公开仓库](https://github.com/Dunoguang/SPRD-Uboot-Patcher)

镜像格式改动应通过已知样本对拍。添加或压缩 payload 后，逐段检查偏移、尺寸、对齐和校验值。把输出交给同一个解析器重新读一遍，再用设备日志核对交接结果。
