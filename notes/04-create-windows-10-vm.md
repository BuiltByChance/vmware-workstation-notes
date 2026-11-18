# 下载 Windows 10 镜像，创建并配置虚拟机

## 1. 准备 Windows 10 ISO

在微软下载页的“创建 Windows 10 安装媒体”下下载并运行媒体创建工具。接受条款，选“为另一台电脑创建安装介质”，再选语言、版本和体系结构。课程用的是**简体中文、Windows 10、64 位（x64）**。需要手动选择时，取消“对这台电脑使用推荐的选项”。最后选“ISO 文件”并保存，供虚拟光驱使用。[微软官方下载页](https://www.microsoft.com/zh-cn/software-download/windows10)

视频中的“最新”指录制时的 1909 版。微软下载页目前提供 22H2，Windows 10 家庭版和专业版的常规支持已于 2025 年 10 月 14 日结束。[微软版本与支持说明](https://www.microsoft.com/zh-cn/software-download/windows10)

## 2. 创建空白虚拟机

在 Workstation 中选 **文件 → 新建虚拟机 → 自定义（高级）**。硬件兼容性按之后要运行这台虚拟机的 Workstation 版本选择。点“稍后安装操作系统”，客户机类型选 **Microsoft Windows → Windows 10 x64**，与 ISO 的体系结构保持一致。[Workstation 创建向导说明](https://knowledge.broadcom.com/external/article/315434/how-to-create-virtual-machines-in-vmware.html)

给虚拟机命名，并在空间充足的 SSD 上给它单独建一个文件夹。已有分区里的普通文件夹就可以存放虚拟机。Windows 和应用装进 `.vmdk` 虚拟磁盘，后续快照也会占用主机空间。

| 配置项 | 课程示例 | 选择时看什么 |
| --- | --- | --- |
| 固件 | UEFI | 在开始安装前选定启动方式。 |
| CPU 和内存 | 2 个处理器 × 每个 2 核，共 4 个虚拟 CPU，内存 4 GB | 按主机可用资源分配，给主机系统和其他程序留出余量。 |
| 网络 | NAT | 客户机通过主机的网络连接上网，适合本节的单机练习。 |
| 虚拟磁盘 | 新建 SCSI 磁盘，最大 40 GB，存为单个文件 | 关闭“立即分配所有磁盘空间”后，磁盘文件随实际写入增长。用来安装系统和开发工具时，要把软件和更新所需空间计入容量。 |

## 3. 从 ISO 启动安装

1. 打开 **虚拟机设置 → CD/DVD → 使用 ISO 映像文件**，选中下载好的 `.iso`，确认“启动时连接”，再开启虚拟机。若出现从光盘启动的按键提示，点进虚拟机按回车。按 `Ctrl + Alt` 可把鼠标和键盘交还给主机。
2. 在 Windows 安装程序中选语言和键盘，点“现在安装”。若要稍后激活，可选“我没有产品密钥”，再选择与自己许可证对应的版本。课程选的是 **Windows 10 专业版 x64**。
3. 选 **自定义：仅安装 Windows**。对于刚创建、整盘空白的虚拟磁盘，可以直接选中“未分配空间”并点“下一步”，由安装程序建立所需分区。课程为了演示分区，把 40 GB 虚拟盘的一半划给系统，得到的 19.4 GB 主分区较小。使用整块虚拟盘可为后续更新和应用留出更多空间。[微软安装分区说明](https://learn.microsoft.com/zh-cn/windows-hardware/manufacture/desktop/windows-setup-installing-using-the-mbr-or-gpt-partition-style)
