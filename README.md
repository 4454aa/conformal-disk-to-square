# Conformal Disk-to-Square Unwrap（圆形→正方形保形展开）

把图片中的**圆形区域**展开为**正方形输出**，尽量保持局部角度（保形/保角）。

> 适用场景：圆形头像/徽标素材整理、纹理对齐与分析、图案展开可视化等。

---


### 输入（圆形区域） vs 输出（正方形展开）

<p align="center">
  <img src="assets/orig.jpg" alt="Input (circular region)" width="45%">
  <img src="assets/mapped.jpg" alt="Output (square unwrap)" width="45%">
</p>


---

## Features

- ✅ 圆形区域 → 正方形展开（WebGL fragment shader）
- ✅ 两种交互模式  
  - 默认：**固定圆框**，拖动/缩放图片（更接近主流裁剪器手感）  
  - 可选：**编辑圆框**（精调圆心/半径）
- ✅ 输出分辨率：默认自适应、上限可调（含“无上限”）
- ✅ 采样/插值：最近邻 / 线性平滑 / mipmap（可用则启用）
- ✅ 一键导出 PNG/JPG

---

## Quick Start

### 在线使用
直接访问：https://4454aa.github.io/conformal-disk-to-square/

### 本地使用
1. 下载或复制 `index.html`
2. 用浏览器打开
3. 上传图片 → 调整圆形区域 → 点击生成 → 下载结果

---

## UI Notes

- **固定圆框模式（默认）**  
  - 拖动：移动图片  
  - 滚轮/捏合：缩放图片
- **编辑圆框模式**  
  - 拖动：移动圆心  
  - 滚轮/捏合：缩放圆半径

---

## Math (High-level)

本项目使用“圆盘 ↔ 正方形”的共形映射（conformal mapping）思路，并在实现上采用 Jacobi Theta 函数的可计算表达，以便在 GPU 中以固定开销评估映射（截断级数近似）。

- Schwarz–Christoffel mapping（圆盘/上半平面 → 多边形）  
  https://zh.wikipedia.org/wiki/%E6%96%BD%E7%93%A6%E8%8C%A8-%E5%85%8B%E9%87%8C%E6%96%AF%E6%89%98%E8%B4%B9%E5%B0%94%E6%98%A0%E5%B0%84
- Lemniscate elliptic functions（与“圆↔方”相关的椭圆函数视角）  
  https://en.wikipedia.org/wiki/Lemniscate_elliptic_functions
- Theta functions（定义/性质/计算：NIST DLMF）  
  https://dlmf.nist.gov/20  
  https://dlmf.nist.gov/20.2
- 讨论链接（MSE）：Conformal mapping between a square and a unit disk?  
  https://math.stackexchange.com/questions/3630031/conformal-mapping-between-a-square-and-a-unit-disk

---

## Motivation（简述）

- 看到维基共享资源中“保形正方形网格”的示意图，想把这种效果做成可交互实验：  
  https://commons.wikimedia.org/wiki/File:Omnitruncated_tiling_on_conformal_square.png
- 许多社交平台头像是圆形裁切；在排版/对比/进一步处理时，方形表示更方便。

---

## License & Credits

- 示例图来自 Wikimedia Commons：许可信息以文件页为准。  
  https://commons.wikimedia.org/wiki/File:Omnitruncated_tiling_on_conformal_square.png
- 数学函数参考：NIST DLMF（Theta functions）  
  https://dlmf.nist.gov/20
