# THE EVOLUTION OF AI · 从图灵纸带到硅基星云（1950 — 2026+）

> 单文件 · 零依赖 · 双击即跑的 **9000 颗粒全粒子史诗动画（Vibe Video）**
> A single-file, zero-dependency, 9000-particle 3D particle epic — pure HTML5 Canvas 2D + hand-written perspective engine.

```
9000 particles = 7500 core morphing particles + 1500 deep-space ambient particles
5 acts · 35 seconds · auto-loop · seekable · Web Audio synthesized score
```

---

## 运行方式 · How to run

**方式一（推荐）**：直接双击 `index.html`（或 `ai-evolution-particle-epic.html`），无需服务器、无需构建、无外部图片/字体/音频文件，因此**不会产生任何 CORS 问题**。

**方式二**：若仓库开启 GitHub Pages（Settings → Pages → Branch: `main` / root），可直接在线观看。

> 打开后动画自动播放；点击右下角 **♪ 音效** 才会启动 Web Audio（浏览器自动播放策略要求一次用户手势）。

---

## 五幕时间轴 · 5-act timeline（35s，自动循环）

| Act | 时间 | 年代 | 主题 | 粒子形态与配色 |
|---|---|---|---|---|
| 01 | 0–7s | 1950–1956 | **SYMBOLIC DAWN** 符号主义黎明 | 机械阶跃拼出 `1950 TURING` + 递归 3D 二叉逻辑树 + 无限格点纸带；复古 CRT 荧光绿（Hue 120–140） |
| 02 | 7–14s | 1974–1986 | **WINTER & PERCEPTRON** 寒冬与连接主义觉醒 | 前 3 秒逻辑树冻结碎裂、重力下沉（字幕 `AI WINTER`）；第 10 秒中心爆发暖橙冲击波，重组为 Input→Hidden→Output 三层垂直神经元圆盘；冰晶暗蓝（Hue 200）→ 炽热暖橙（Hue 25–45），误差梯度脉冲在层间往返（Backpropagation） |
| 03 | 14–21s | 2012–2016 | **DEEP LEARNING & ALPHAGO** 深度学习与落子无悔 | 镜头俯冲进入 19×19 悬浮棋盘＋AlexNet 卷积金字塔；金色星雨落向交叉点并激起涟漪，第 37 手为高亮金色脉冲核心（`MOVE 37`），上空数道蒙特卡洛搜索光柱；深空蓝＋曜石金（Hue 220 & 48） |
| 04 | 21–28s | 2017–2022 | **ATTENTION IS ALL YOU NEED** 大模型的诞生 | 棋盘向外炸开并卷曲成双层同心三维注意力星环（8 个注意力头）；数千条半透明发光 Self-Attention 权重连线高速闪烁；环心凝聚出 `GPT / LLM` 粒子字样；赛博青＋洋红霓虹（Hue 180 & 300） |
| 05 | 28–35s | 2023–2026+ | **MULTIMODAL SINGULARITY** 多模态涌现 | 引力坍缩 → 超新星爆发 → 球面斐波那契网格＋3D 简谐噪声构建左右双半球“硅基大脑星云”（呼吸律动、皮层突触连线），最终凝聚为 `INTELLIGENCE UNBOUND` 粒子巨幕；星云紫＋全光谱白光（Hue 260–320） |

---

## 交互 · Controls

| 操作 | 效果 |
|---|---|
| 鼠标划过 | 径向排斥力场 + 涟漪冲击环 |
| 按住拖拽 | 自由旋转 3D 观察视角 |
| 按住鼠标 | 力场由“排斥”反转为“吸引” |
| 滚轮 | 推拉镜头（按幕限幅） |
| 空格 / 播放键 | 暂停 / 播放 |
| `1`–`5` / 底部纪元按钮 / 右侧章节点 | 跳转到对应历史纪元 |
| 进度条点击·拖拽 | 任意时刻无级 seek（含状态重建） |
| `←` `→` | ±2 秒 |
| `H` | 隐藏 / 显示全部 HUD |
| `R` | 回到起点 |
| `♪ 音效` | 开关 Web Audio 合成配乐 |

---

## 技术实现 · Engineering notes

* **手写 3D 引擎**：透视投影 + 相机偏航/俯仰/滚转矩阵 + 景深剔除；`devicePixelRatio` 自适应并以 2.55MPix 像素预算限幅，焦距随分辨率缩放，构图在 CSS 像素空间恒定。
* **两套目标点生成机制**：
  1. `sampleText()` — 离屏 Canvas 绘制文字/符号 → `getImageData` 采样 → 映射到 3D 平面（戏剧化的打乱采样 + 深度抖动形成体积感）；
  2. `genTree / genTape / genWinter / genMLP / genBoard / genRing / genNebula` — 纯数学公式生成 3D 点云 `(tx, ty, tz, hue, connectGroup)`。
* **连贯 Morph**：装配前对粒子与目标按极角排序后一一对应，得到旋转式变形而非乱线穿插；第一幕使用晶格量化 + 逐粒子延迟形成“机械阶跃”质感。
* **渲染管线**：`globalCompositeOperation = 'lighter'` 发光叠加 + 帧间半透明残影；按「色相 × 尺寸 × 透明度」288 桶计数排序批量绘制（小粒子 `fillRect`、大粒子 `arc` + 光晕），并按幕调节残影衰减以保持深空对比度。
* **确定性**：`mulberry32` 式 LCG 伪随机，`__AI.seek(t)` 可重建任意时刻状态、`__AI.audit()` 输出逐幕断言、`__AI.fingerprint()` 输出状态指纹。
* **Web Audio 合成配乐**（无音频文件）：第一幕 8-bit 脉冲打字机滴答；第二幕带通滤波白噪音寒风；第三–五幕汉斯·季默式大三和弦 Drone（失谐锯齿 + 慢速滤波 LFO + 反馈延迟），转场触发 Sub-bass Drop 与噪声上升气流，随幕切换和弦与增益总线。
* **HUD**：毛玻璃胶囊控制台、纪元跳转、进度条、字幕机（双语微字幕）、章节指示、CRT 扫描线（仅第一幕）。

---

## 自动化验证 · Verified results

使用无头 Chrome (154) + 原生 CDP 协议驱动真机页面（`file://` 直开），逐幕 seek 截屏 + 断言：

```
AUDIT (each act @ t0+4.2s)      nan=0   visible=7500/7500
act1  meanR=410  meanHue=131   act2  meanR=313  meanHue=42
act3  meanR=668  meanHue=228   act4  meanR=374  meanHue=246  links=3748
act5  meanR=312  meanHue=282   links=222
EXCEPTIONS: none      ERROR LOGS: none
full 40s playthrough: acts [1,2,3,4,5] → loop wrap OK
controls: era/play/pause/keyboard/wheel/drag OK · audio graph built OK
HiDPI (DPR2 @1920×1080): canvas 2129×1198, no exceptions
```

截图见 [`screenshots/`](screenshots)（含 `montage.png` 九宫格总览）。

---

## 文件 · Files

| 文件 | 说明 |
|---|---|
| [`index.html`](index.html) | 完整单文件动画（推荐直接双击） |
| [`ai-evolution-particle-epic.html`](ai-evolution-particle-epic.html) | 同上，同名副本便于本地留存 |
| [`screenshots/`](screenshots) | 逐幕验证截屏 |

> 全部 HTML/CSS/JS 内联，无 CDN、无外部字体、无图片、无音频文件。

---

## 调试 API

```js
window.__AI.seek(17.5)     // 无级跳转并重建该时刻完整状态
window.__AI.audit()        // 逐幕断言：NaN / 可见粒子 / 半径 / 色相 / 连线数
window.__AI.state()        // 运行态快照
window.__AI.fingerprint()  // 状态指纹（回归比对用）
```
URL 参数：`?t=12.5&paused=1&hud=0&audio=1`。

MIT License.
