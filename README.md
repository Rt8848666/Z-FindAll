# Z-FindAll

> Windows Prefetch 文件分析与安全日志取证工具

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-Windows%2010%7C11-lightgrey.svg)]()
[![Python](https://img.shields.io/badge/python-3.8+-green.svg)]()

## 📖 简介

Z-FindAll 是一款专业的 Windows Prefetch 文件分析与安全日志取证工具，专为数字取证、安全审计和系统运维人员设计。工具采用图形化界面，无需专业知识即可快速分析程序执行历史和系统登录事件。

## ✨ 核心功能

### 🔍 Prefetch 文件分析
- 自动读取 `C:\Windows\Prefetch` 目录下的所有 `.pf` 文件
- 解析程序执行信息：程序名称、运行次数、最后运行时间
- 提取关联文件路径：显示程序运行时访问的所有文件
- 支持自定义目录扫描

### 🔐 安全日志分析
- 解析 Windows 安全事件日志（Security.evtx）
- 检测 RDP 远程登录事件（EID 4624/4625）
- 识别登录成功/失败记录
- 提取登录用户、来源 IP、登录时间等关键信息

### 🔎 全文搜索
- 支持关键字模糊搜索
- 跨所有字段检索（程序名、文件路径、事件 ID 等）
- 实时高亮显示匹配结果

### 🎨 用户体验
- 清爽的浅蓝色主题 + 深色模式切换
- 固定窗口尺寸 1280x800，适配主流显示器
- 一键复制所有数据（单元格/行/全部）
- 自动保存扫描结果为 JSON 格式

## 📦 下载安装

### 方式一：下载安装包

1. 访问 [Releases 页面](https://github.com/RT886/Z-FindAll/releases)
2. 下载最新版本的 `Z-FindAll-vX.X.exe`
3. 双击运行即可（无需安装）



## 🚀 使用说明

### 快速开始

1. **启动程序**
   - 双击运行 `Z-FindAll.exe`
   - 首次运行会提示需要管理员权限，点击"是"

2. **Prefetch 分析**
   - 默认显示 Prefetch 分析页面
   - 程序自动加载 `C:\Windows\Prefetch` 目录
   - 查看程序列表：程序名称 | 运行次数 | 最后运行时间
   - 点击任意程序查看详细文件路径

3. **安全日志分析**
   - 切换到"安全日志"标签页
   - 树形结构展示登录事件
   - 展开节点查看详细信息
   - 红色 = 登录失败，绿色 = 登录成功

4. **全文搜索**
   - 切换到"搜索"标签页
   - 输入关键字后点击"刷新"
   - 查看匹配的所有记录

### 右键菜单功能

| 页面 | 右键功能 |
|------|----------|
| Prefetch 列表 | 复制整行 / 复制单元格 |
| 详情列表 | 复制全部路径 / 复制选中行 |
| 安全日志树 | 复制此项 / 复制所有列 |
| 搜索结果 | 复制此项 / 复制所有列 |

### 快捷键

| 快捷键 | 功能 |
|--------|------|
| `Ctrl+C` | 复制当前选中内容 |
| `Ctrl+S` | 保存扫描结果 |

### 数据导出

扫描结果自动保存为 JSON 格式，保存位置：
- **默认路径**：程序所在目录
- **文件格式**：`Z-FindAll_扫描结果_YYYYMMDD_HHMMSS.json`

## 🔧 系统要求

| 项目 | 要求 |
|------|------|
| 操作系统 | Windows 10 / 11 |
| 权限 | 管理员权限（访问 Prefetch 目录和安全日志必需） |
| 屏幕分辨率 | 最低 1280x800 |
| .NET Framework | Windows 自带（无需单独安装） |
| 磁盘空间 | 至少 50MB 可用空间 |

### 可选依赖

如需解析安全日志（.evtx 文件），需要安装 python-evtx 库：

```bash
pip install python-evtx
```

> 💡 **提示**：已打包的 EXE 已包含所有依赖，无需额外安装。

## 📁 文件结构

```
Z-FindAll/
├── Z-FindAl.exe                     #主程序
├── prefetch_XXX_XXX.json            # 程序运行记录缓存
├── seclog_XXX_XXX.json              # 系统日志缓存

```

## 🎯 应用场景

### 数字取证
- 调查可疑程序的执行历史
- 追踪恶意软件的活动轨迹
- 分析用户操作时间线

### 安全审计
- 检测异常登录行为
- 审计 RDP 远程访问记录
- 排查暴力破解尝试

### 系统运维
- 统计常用程序使用情况
- 清理长期未运行的程序
- 优化系统启动项

## ⚠️ 注意事项

1. **管理员权限**：程序需要管理员权限才能访问系统日志和 Prefetch 目录
2. **数据隐私**：本工具仅读取本地数据，不会上传任何信息
3. **兼容性**：仅支持 Windows 系统，不支持 macOS/Linux
4. **日志文件**：安全日志默认位于 `C:\Windows\System32\winevt\Logs\Security.evtx`

## 🐛 常见问题

### Q: 提示"拒绝访问"？
A: 右键点击 EXE，选择"以管理员身份运行"

### Q: 安全日志页面显示"未安装依赖库"？
A: 已打包的 EXE 已包含依赖。如自行打包，请确保安装 `python-evtx`

### Q: Prefetch 目录为空？
A: 检查系统是否启用了 Prefetch 功能（某些 SSD 优化可能禁用）

### Q: 窗口显示不完整？
A: 调整屏幕分辨率至 1280x800 或更高，或调整 DPI 缩放

### Q: 如何反馈问题？
A: 在 GitHub 仓库提交 [Issue](https://github.com/RT886/Z-FindAll/issues)

## 📄 许可证

本项目采用 MIT 许可证。详见 [LICENSE](LICENSE) 文件。

## 📬 联系方式

- 作者：RT886
- 项目地址：https://github.com/RT886/Z-FindAll
- 问题反馈：https://github.com/RT886/Z-FindAll/issues

## 🙏 致谢

感谢所有为本项目贡献代码和反馈的用户！

---

<div align="center">

**如果这个项目对你有帮助，请给一个 ⭐️ Star！**

</div>
