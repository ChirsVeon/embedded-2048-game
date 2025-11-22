# 2048-C

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

一个在嵌入式Linux平台上运行的2048游戏实现，专为触摸屏设备设计。本项目是嵌入式系统与设计实训课程的实践项目，通过C语言实现了完整的2048游戏逻辑，并在开发板上进行了性能优化和调试。

## 🚀 项目特点

- **嵌入式优化**：专为资源受限的嵌入式设备设计，代码精简高效
- **触摸屏交互**：支持触摸屏滑动操作，提供流畅的用户体验
- **LCD直接驱动**：绕过高级图形库，直接操作LCD屏幕，减少系统开销
- **BMP图像支持**：支持BMP格式图片显示，实现美观的游戏界面
- **性能分析**：针对嵌入式平台进行性能优化，确保流畅运行
- **模块化设计**：清晰的代码结构，便于维护和功能扩展

## ⚙️ 技术栈

- **编程语言**: C语言
- **开发环境**: Linux
- **硬件平台**: 嵌入式开发板
- **核心功能**:
  - LCD屏幕驱动
  - BMP图像处理
  - 触摸屏输入处理
  - 2048游戏算法实现
  - 随机数生成与位置管理

## 🖥️ 硬件要求

- 嵌入式Linux开发板（如ARM架构）
- 支持的LCD屏幕（分辨率建议800x480或更高）
- 电容式或电阻式触摸屏
- 最小8MB存储空间

## 📦 软件依赖

- Linux内核（建议4.x版本或更高）
- GCC编译器
- 标准C库
- Framebuffer驱动支持

## 🛠️ 编译与运行

### 编译步骤

```bash
# 克隆项目
git clone https://github.com/ChirsVeon/embedded-2048-game.git
cd embedded-2048-game

# 编译项目
make

# 或者手动编译
gcc -o 2048 main.c lcd.c bmp.c -lm -I.
```

### 运行步骤

```bash
# 确保有执行权限
chmod +x 2048

# 运行游戏（需要root权限访问设备文件）
sudo ./2048
```

### 清理编译文件

```bash
make clean
```

## 📂 项目结构

```
embedded-2048-game/
├── src/                  # 源代码目录
│   ├── main.c           # 主程序，游戏逻辑实现
│   ├── lcd.c            # LCD屏幕驱动和显示功能
│   ├── bmp.c            # BMP图片加载和显示功能
│   └── touch.c          # 触摸屏输入处理
├── include/             # 头文件目录
│   ├── lcd.h            # LCD功能头文件
│   ├── bmp.h            # BMP功能头文件
│   └── touch.h          # 触摸屏功能头文件
├── assets/              # 资源文件
│   └── 2048bmp/         # 游戏BMP图片资源
│       ├── background.bmp
│       ├── game_over.bmp
│       ├── 2.bmp
│       ├── 4.bmp
│       └── ...          # 其他数字图片
├── Makefile             # 编译脚本
├── README.md            # 项目说明文档
└── LICENSE              # 许可证文件
```

## 🎮 游戏规则

1. **目标**：通过滑动合并相同数字的方块，最终得到2048方块
2. **操作**：在触摸屏上滑动（上、下、左、右）来移动所有方块
3. **合并**：相同数字的方块在移动方向上会合并成一个更大的方块
4. **新增**：每次有效移动后，会在空白位置随机生成一个2或4
5. **结束**：当棋盘填满且没有可合并的方块时，游戏结束

## 📝 代码说明

### 核心功能

- **`getRand()`**: 在空白位置随机生成2或4
- **`gameOver()`**: 检查游戏是否结束
- **`startGame()`**: 初始化游戏状态
- **`up()`/`down()`/`left()`/`right()`**: 四个方向的移动算法
- **`showGameBmp()`**: 根据游戏状态更新显示

### LCD与图像处理

- **`initLcd()`**: 初始化LCD屏幕
- **`uninitLcd()`**: 释放LCD资源
- **`showBmp()`**: 显示BMP格式图片
- **`showGameBmp()`**: 根据游戏矩阵显示对应数字图片

## 🐞 常见问题

### 1. 无法打开LCD设备
```bash
sudo chmod 666 /dev/fb0
```
或确保以root权限运行程序。

### 2. 图片显示异常
检查`assets/2048bmp/`目录是否存在，且BMP图片格式正确。

### 3. 触摸屏无响应
确认触摸屏设备文件路径是否正确，通常为`/dev/input/event0`或类似路径。

## 🤝 贡献指南

欢迎贡献代码！请遵循以下步骤：

1. Fork本项目
2. 创建新分支 (`git checkout -b feature/your-feature`)
3. 提交更改 (`git commit -am 'Add some feature'`)
4. 推送到分支 (`git push origin feature/your-feature`)
5. 创建Pull Request

## 📄 许可证

本项目采用 [MIT License](LICENSE) 开源许可。

## 🙏 致谢

- 感谢嵌入式系统与设计实训课程提供学习机会
- 感谢所有为开源2048游戏贡献代码的开发者
- 特别感谢Linux社区提供的优秀开发环境和工具

## 📧 联系方式

- 作者: ChirsVeon
- 邮箱: [YiQingOfficial@163.com](mailto:YiQingOfficial@163.com)
- GitHub: [@ChirsVeon](https://github.com/ChirsVeon)

---

**Enjoy the game!** 🎮
