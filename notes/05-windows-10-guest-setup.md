# Windows 10 首次设置、VMware Tools、激活与数据盘

## 完成首次设置

恢复上节的 Windows 10 虚拟机，按首次启动向导选择区域和键盘。需要测试中英文输入时，可以添加“英语（美国）”键盘。视频使用的 Windows 10 专业版 1909 可通过“针对个人使用进行设置 → 脱机帐户 → 有限的体验”创建本地用户。位置、语音识别、广告 ID 等隐私选项可按测试需要选择。

进入桌面后，在“此电脑 → 属性”核对 Windows 版本、系统类型和内存。视频中的客户机是 **Windows 10 专业版、64 位、4 GB 内存**。在文件资源管理器的“查看”中勾选“文件扩展名”，方便辨认安装包、压缩包和脚本。

## 安装 VMware Tools，让桌面随窗口缩放

1. 启动并登录客户机。在主机的 Workstation 菜单中选 **虚拟机 → 安装 VMware Tools**。Workstation 会把 Tools 安装光盘挂载到客户机。
2. 在客户机内打开“此电脑”，双击标为 **VMware Tools** 的 DVD 驱动器，运行安装向导。课程使用“典型”安装，完成后按提示重启客户机。[Broadcom 安装说明](https://knowledge.broadcom.com/external/article/315363/installing-and-upgrading-vmware-tools-in.html)
3. 拖动 Workstation 窗口边缘或切换全屏，检查客户机桌面能否自动适配。若需传文件且已启用拖放，可从主机拖一个普通文件到客户机桌面验证。要保留刚装好系统和 Tools 的状态，可在此时拍一张快照。[快照的使用方法](02-virtual-machine-basics.md)

## 核对 Windows 激活状态

在**客户机内**打开 **设置 → 更新和安全 → 激活**。已有适用于这台虚拟机和所装 Windows 版本的数字许可证时，联网后核对状态。有产品密钥时，选“更改产品密钥”，输入与版本匹配的 25 位密钥。[微软激活说明](https://support.microsoft.com/zh-cn/windows/activation/activate-windows)

## 把虚拟磁盘剩余空间建成数据盘

如果上节安装时留了未分配空间，在**客户机内**右键“开始”打开“磁盘管理”，找到虚拟磁盘上标为“未分配”的区域，右键选“新建简单卷”。选择卷大小和可用盘符，以 NTFS 格式化这个新卷并填写卷标。视频中 `D:` 已由虚拟光驱占用，新卷命名为 `Develop`，完成后在“此电脑”中显示为 `Develop (E:)`，容量约 19.9 GB。[微软磁盘管理说明](https://support.microsoft.com/zh-cn/windows/experience/storage-filemanagement/disk-management-in-windows)

## 让客户机使用 USB 设备

在 Workstation 的 **虚拟机 → 可移动设备** 中选中目标 USB 设备，点击“连接（断开与主机的连接）”。如果希望每次插入时再决定交给哪一边，在 **编辑 → 首选项 → USB** 中选择“询问我执行的操作”。
