# DSP-Based Measurement System

📐 **项目描述**：
该设计参考2023年全国大学生电子设计大赛C题，采用 TMS320F28335 制作。普通的 MCU 单片机计算效率低下，因此采用 DSP 完成。显示器件为 LCD1602。

![测量显示图]![image](https://github.com/pieceofApple/DSPF28335_FFT-/assets/116827010/fce5133c-74ee-426a-b2ca-c213267ea5cb)


## 核心设计
- **核心芯片**: TMS320F28335
- **显示器件**: LCD1602
- **运算放大器**: LF347（4个）

## 设计说明
🔧 **电路设计**:
借鉴 TIDA-060029 文档中的电路设计，核心思想是 IV 分离电路，但采用了自主平衡阻抗和更优良的补偿机制。

📄 **参考文档**:
[TIDA-060029 文档](https://www.ti.com.cn/cn/lit/ug/zhcu794b/zhcu794b.pdf?ts=1717917139311&ref_url=https%253A%252F%252Fwww.ti.com.cn%252Fsitesearch%252Fzh-cn%252Fdocs%252Funiversalsearch.tsp%253FlangPref%253Dzh-CN)

由于现有器件限制，使用的运放为 LF347，刚好4个够用。运放电路较为简单，并未采用补偿机制，但测量精度尚可。由于电路的非理想特性，若不采用补偿机制，只能通过后期 FFT 所得参数进行拟合调教。

## 硬件组件
- **TMS320F28335**: 高性能 DSP
- **LCD1602**: 显示模块
- **LF347**: 四运放芯片(性能堪堪够用，频率过高则需考虑衰减)

## 功能介绍
- 🌐 **高效计算**: 采用 DSP 提高计算效率
- 📊 **精确测量**: 通过自定义电路实现高精度测量
- 🖥️ **实时显示**: 使用 LCD1602 实时显示测量数据

## 连接示例
```plaintext
TMS320F28335    LCD1602   LF347
VCC             VCC       VCC
GND             GND       GND
SDA             SDA       -
SCL             SCL       -
...
