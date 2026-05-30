# Shadowsocks Rust 配置指南

Shadowsocks Rust 是用 Rust 重写的高性能版本，比原版 Python 版本快数倍。

## 为什么选择 ss-rust

- 高性能: Rust 实现，速度极快
- 低内存: 资源占用极小
- 安全: 支持 AEAD 加密
- 简单: 配置文件简洁

## 安装

```bash
# Linux x86_64
wget https://github.com/shadowsocks/shadowsocks-rust/releases/latest/download/shadowsocks-v2ray-plugin-linux-x86_64.tar.xz
tar -xf shadowsocks-vust-linux-x86_64.tar.xz
mv ssserver /usr/local/bin/

# 或使用 Docker
docker run -d --name ss -p 8388:8388 -p 8388:8388/udp \
  -e PASSWORD=your-password -e METHOD=chacha20-ietf-poly1305 \
  --restart always ghcr.io/shadowsocks/ssserver-rust:latest
```

## 配置文件

```json
{
  "server": "0.0.0.0",
  "server_port": 8388,
  "password": "your-password",
  "method": "chacha20-ietf-poly1305",
  "mode": "tcp_and_udp",
  "timeout": 300,
  "fast_open": true
}
```

## 加密方式选择

| 加密方式 | 速度 | 安全 | 推荐 |
|---------|------|------|------|
| aes-256-gcm | 快 | 高 | 推荐 |
| chacha20-ietf-poly1305 | 中 | 高 | 移动端推荐 |

## 常见问题

**连接被重置？** 使用 v2ray-plugin 混淆 TLS 流量。

**速度慢？** 使用 aes-256-gcm，服务器开启 BBR。

---

推荐工具：

- [Clash for Windows](https://clashforwindows.site/)
- [ClashMI](https://clashmi.site/)
- [FlClash](https://flclash.us/)
