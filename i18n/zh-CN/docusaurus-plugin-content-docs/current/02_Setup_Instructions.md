---
sidebar_position: 2
title: 2. 设置说明
---

## 功能使用说明

### VoidChain 通信架构

**边缘信任机器下载路径：**

Windows 版本：
```
http://www.xxx.com/download/tmac_win.rar
```

Linux 版本：
```
http://www.xxx.com/download/tmac_linux.tar
```

### 使用说明

首先在 `chain.conf` 中配置连接参数：

- **Data_dir**：已有数据目录，无空间要求，几乎不占用空间
- **tmac_entry**：VoidChain 网络信任机器接入信息

### Windows 启动方式
```
Drive:/pathname/guard_tmac.exe
```

### Linux 启动方式
```bash
nohup /pathname/guard_tmac.exe &
```

### Postman 接口操作方法

如果使用本地机器，接口地址为：
```
http://127.0.0.1:8080
```
