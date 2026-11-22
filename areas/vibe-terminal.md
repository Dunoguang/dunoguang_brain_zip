# 终端 MCP 与 Android 容器

VibeTerminalMCP 的 Rust 版围绕 PTY 读写、会话管理、输出限长和审计功能维护。测试时同时覆盖中文输入、中文输出、二进制流、超长输出和高频回显。 [VibeTerminalMCP-Rust](https://github.com/Dunoguang/VibeTerminalMCP-Rust)

VibeGo 关注在 Android 上运行 LXC 与 systemd。验收要同时检查命名空间、挂载、容器里的服务状态和板级内核支持。曾用 Arch Linux ARM rootfs 验证 systemd 能启动。 [VibeGo](https://github.com/Dunoguang/VibeGo)
