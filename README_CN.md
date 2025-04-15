# RGB通道混合器 (RGB Crosstalk)

这是一个为DaVinci Resolve创建的DCTL插件，用于精确控制RGB通道之间的混合比例。

![RGB通道混合器界面](images/RGB_Crosstalk.png "RGB通道混合器插件界面")

## 功能特点

### 核心机制
- 保持每个输出通道的色彩贡献总和恒定为1，维持整体亮度和色彩平衡。
- 调整时保持中性色不变，简化传统RGB混合器的工作流程。

### 精确控制与效果
- 允许精确调整每个输入通道对各输出通道的贡献比例。
- 支持负值参数以实现创意效果和色彩交互。

### 易用性
- 提供直观的滑块用户界面。
- 鼓励通过观察矢量示波器变化进行实验性学习，即使不深入了解RGB混合器理论。

## 参数说明

插件提供了6个滑块参数，每个参数范围为-1.0到1.0，分别控制：

- **Green in Red**: 调整绿色通道对红色输出的贡献比例
- **Blue in Red**: 调整蓝色通道对红色输出的贡献比例
- **Red in Green**: 调整红色通道对绿色输出的贡献比例
- **Blue in Green**: 调整蓝色通道对绿色输出的贡献比例
- **Red in Blue**: 调整红色通道对蓝色输出的贡献比例
- **Green in Blue**: 调整绿色通道对蓝色输出的贡献比例

插件会自动计算每个通道对自身输出的贡献比例，确保：
- Red in Red = 1 - (Green in Red) - (Blue in Red)
- Green in Green = 1 - (Red in Green) - (Blue in Green)
- Blue in Blue = 1 - (Red in Blue) - (Green in Blue)

设置负值可以创建更多创意效果和颜色交互。例如，设置Blue in Red = -0.114会减弱红色通道中蓝色的贡献。

## 安装方法

1. 将`RGB_Crosstalk.dctl`文件复制到DaVinci Resolve的LUT目录：
   - Windows: `C:\ProgramData\Blackmagic Design\DaVinci Resolve\Support\LUT`
   - macOS: `/Library/Application Support/Blackmagic Design/DaVinci Resolve/LUT`
   - Linux: `/opt/resolve/LUT`

2. 重启DaVinci Resolve（如果已运行）

## 使用方法

1. 在Color页面，打开OpenFX面板
2. 找到"ResolveFX Color">"DCTL"效果
3. 将DCTL效果拖到一个节点上
4. 在Inspector面板中，从DCTL List下拉列表中选择"RGB_Crosstalk"

## 应用场景

- 创建特殊的颜色风格和色彩效果
- 修复颜色不平衡问题
- 创造性地调整影像颜色氛围
- 实现更精细的交叉色彩控制，包括通过负值创建颜色对比 