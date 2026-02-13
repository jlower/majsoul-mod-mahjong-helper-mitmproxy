
# MajsoulMax VPS 部署指南 by 无限

本文档旨在指导如何在 Linux VPS 上部署 MajsoulMax 服务，实现全平台（以 iOS 为例）解锁全角色、皮肤、装扮等功能。

## 一、 系统环境准备

在开始之前，建议使用 Debian 12+ 系统，并确保已安装 `git` 和 `curl`。

### 1. 安装 UV 依赖管理工具

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
source $HOME/.cargo/env
```

### 2. 克隆项目与环境初始化

```bash
cd /opt
sudo git clone https://github.com/Avenshy/MajsoulMax.git
cd MajsoulMax

# 创建虚拟环境并同步依赖
uv venv
source .venv/bin/activate
uv pip install -r requirements.txt
```

------

## 二、 证书配置与系统信任

由于项目基于 MITM（中间人攻击）原理，VPS 自身也需要信任生成的根证书以确保链路完整。

### 1. 生成初始证书

运行一次 `mitmdump` 以自动在本地生成 CA 证书文件。

```bash
uv run mitmdump
```

### 2. 系统信任 CA 证书

将生成的证书拷贝至系统目录并更新信任列表：

```bash
# 拷贝至系统证书目录
sudo cp ~/.mitmproxy/mitmproxy-ca-cert.cer /usr/local/share/ca-certificates/mitmproxy.crt

# 更新系统信任库
sudo update-ca-certificates

# 验证安装是否成功
# 如果返回 "subject=CN = mitmproxy" 则表示成功
openssl crl2pkcs7 -nocrl -certfile /etc/ssl/certs/ca-certificates.crt | openssl pkcs7 -print_certs -noout | grep "mitmproxy"
```

------

## 三、 持久化服务配置 (Systemd)

为了保证服务在后台稳定运行并在宕机后自动重启，建议使用 Systemd 进行管理。

### 1. 创建 Service 文件

创建文件 `/etc/systemd/system/majsoulmax.service`：

```ini
[Unit]
Description=MajsoulMax Mitmproxy Service
After=network.target

[Service]
Type=simple
WorkingDirectory=/opt/MajsoulMax
# 请根据实际 uv 安装路径调整 ExecStart
ExecStart=/root/.local/bin/uv run mitmdump -p 23410 -s addons.py --set block_global=false
Restart=on-failure
RestartSec=5s
User=root
# 注入环境变量以确保 Python 解释器可见
Environment="PATH=/root/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

[Install]
WantedBy=multi-user.target
```

### 2. 启动与开机自启

```bash
sudo systemctl daemon-reload
sudo systemctl enable --now majsoulmax.service

# 查看运行状态
sudo systemctl status majsoulmax.service
```

------

## 四、 客户端配置 (以 iOS 为例、其他设备参照官网使用 Mihomo 分流)

### 1. 证书安装与信任

1. **获取证书**：从 VPS 的 `/root/.mitmproxy/mitmproxy-ca-cert.cer` 导出至手机。
2. **安装描述文件**：在文件中打开描述文件 -> 提示“已下载描述文件” -> 进入 `设置` -> `已下载描述文件` -> 点击 `安装`。
3. **完全信任**：进入 `设置` -> `通用` -> `关于本机` -> `证书信任设置` -> 勾选 **mitmproxy** 开关。

### 2. 分流策略配置

以 **Loon** 为例，其他代理软件同理：

- **新增节点**：
  - 别名：`MajsoulMax`
  - 地址：`你的服务器IP`
  - 端口：`23410`
- **配置分流规则**： 将以下规则添加至你的规则集，并将策略指向上述节点。

```list
DOMAIN-KEYWORD,majsoul
DOMAIN-KEYWORD,maj-soul
DOMAIN-KEYWORD,mahjongsoul.com
DOMAIN-KEYWORD,catmjstudio
```
