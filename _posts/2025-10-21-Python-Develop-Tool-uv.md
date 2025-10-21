---
title: Python开发利器 - uv
description: >-
  Python开发利器 - uv
author: YongboStudio
date: 2025-10-21 15:10:00 +0800
categories: [Python, Develop]
tags: [Python, Develop]
pin: true
media_subpath: ''
---

### 工具部署
#### 一键安装
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```
```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

### 手工安装
1. 打开页面：https://github.com/astral-sh/uv/releases/
2. 下载对应版本

### 镜像源修改
#### 全局修改
Windows：`%APPDATA%\uv\uv.toml`
```powershell
mkdir `%APPDATA%\uv\
```

Linux/macOS：`~/.config/uv/uv.toml`
```bash
mkdir -p ~/.config/uv/
```
##### 腾讯源
```bash
cat <<EOF > ~/.config/uv/uv.toml
[[index]]
url = "https://mirrors.cloud.tencent.com/pypi/simple"
name = "tencent"
default = true

[[index]]
url = "https://mirrors.aliyun.com/pypi/simple"
name = "aliyun"
default = false

[[index]]
url = "https://pypi.tuna.tsinghua.edu.cn/simple"
name = "tsinghua"
default = false
EOF
```

##### 项目级别的源设定
```ini
# 默认使用腾讯云源，加速依赖安装
[[tool.uv.index]]
url = "https://mirrors.cloud.tencent.com/pypi/simple"
name = "tencent"
default = true

# 备用：阿里云源
[[tool.uv.index]]
url = "https://mirrors.aliyun.com/pypi/simple"
name = "aliyun"
default = false

# 备用：清华源
[[tool.uv.index]]
url = "https://pypi.tuna.tsinghua.edu.cn/simple"
name = "tsinghua"
default = false

# 官方 PyPI 源
[[tool.uv.index]]
url = "https://pypi.org/simple"
name = "pypi"
default = false

```

##### 查看配置
```bash
cat ~/.config/uv/uv.toml
```

#### 通过命令行临时指定
在运行 `uv` 命令时，可以直接指定镜像源：
```bash
uv add --default-index https://mirrors.cloud.tencent.com/pypi/simple <包名>
```


| 平台              | 配置文件路径             | 一键创建目录            |
| ----------------- | ------------------------ | ----------------------- |
| **Windows**       | `%APPDATA%\\uv\\uv.toml` | `mkdir %APPDATA%\\uv`   |
| **Linux / macOS** | `~/.config/uv/uv.toml`   | `mkdir -p ~/.config/uv` |
