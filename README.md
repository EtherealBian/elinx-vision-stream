# eLinex Vision Stream

[中文](#中文) · [English](#english)

![eLinex vision pipeline](docs/project-overview.png)

## 中文

2026 年全国大学生集成电路创新创业大赛国奖项目的开源整理版。OV5640 采集视频，eLinex FPGA 执行实时图像处理，PyQt6 上位机通过串口切换算法并接收 UDP 图像。

**数据通路**。颜色转换和算法选择后，系统支持 SDRAM 帧缓存、HDMI 显示及 UDP RGB565 图传。基础工程覆盖缩放、旋转、形态学和 Sobel，增强工程覆盖暗光增强和引导滤波等算法。上位机按 1024 × 600 RGB565 组帧，监听 UDP 8080。

### 运行与构建

```powershell
python -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe host/main.py
```

使用 eLinex/eHiWay 工具打开[基础工程](fpga/base/ov5640.qpf)或[增强工程](fpga/enhancement/ov5640.qpf)，目标器件为 EP1S80F1508C6。上位机串口默认 1,000,000 baud，控制帧为 `AA 主模式 子模式 55`。

[系统架构与协议](docs/ARCHITECTURE.md) · [算法索引](docs/ALGORITHM_INDEX.md) · [上位机说明](docs/HOST_SOFTWARE.md) · [第三方说明](THIRD_PARTY_NOTICES.md)

## English

This FPGA vision system combines an OV5640 camera, eLinex image processing, and a PyQt6 host. The design supports color conversion, geometric transforms, spatial filtering, edge detection, and enhancement. It uses SDRAM buffering, HDMI display, and RGB565 video over UDP. The host switches modes over UART and offers preview, snapshots, and recording.

Run the commands under [运行与构建](#运行与构建). Open the base or enhancement QPF in the eLinex/eHiWay tools for EP1S80F1508C6. The host expects 1024 × 600 RGB565 on UDP 8080 and uses a 1,000,000-baud UART for mode commands. See the [protocol](docs/ARCHITECTURE.md), [algorithm index](docs/ALGORITHM_INDEX.md), and [third-party notices](THIRD_PARTY_NOTICES.md).
