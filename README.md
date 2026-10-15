# 《断舍离·DAN-SHA-RI》 4K 电影级 Web3D 艺术短片

> **“断绝不需要的执念，舍弃多余的负累，脱离对外物的执着。”**  
> 一部运行在纯浏览器环境下的 30 秒 4K 电影级 Web3D 视听叙事短片。

![Pipeline 4K UHD](https://img.shields.io/badge/Resolution-4K%20UHD%20(3840%C3%972160)-00f0ff?style=for-the-badge)
![FPS](https://img.shields.io/badge/FrameRate-60%20FPS-ffd700?style=for-the-badge)
![Tech Stack](https://img.shields.io/badge/Three.js-PostProcessing%20Bloom-ff0055?style=for-the-badge)
![Audio](https://img.shields.io/badge/WebAudio-Realtime%20Synthesizer-00ff88?style=for-the-badge)

---

## 🌟 核心特性

- **电影级光影与叙事节奏**：
  - 基于 Three.js ACESFilmic 色调映射 + UnrealBloomPass 辉光特效。
  - 四幕完整视听叙事结构（Act I 囚困执念 ➔ Act II 虚实裂解 ➔ Act III 核心爆发 ➔ Act IV 虚空明镜 ➔ 尾声）。
  - 动态呼吸镜头推进、空间粒子涡流、几何曼陀罗动态解构。
- **纯代码实时音频合成（Web Audio API）**：
  - 零外部音频文件依赖，纯代码实时合成沉浸式 30 秒低频暗黑 Ambient Drone 与空间混响。
  - 在第 8 秒精准触发温润空灵的“磬/铜铃”清脆撞击回响。
- **4K 60FPS 原生 In-Canvas 录制与导出**：
  - 解决浏览器 DOM 无法录入视频的难题，构建了独立的 2D 正交 HUD 光栅化合成器。
  - 2.39:1 电影宽银幕黑边（Letterbox）、四幕金句字幕、微柔光晕（Halo Stroke）以及 HUD 时间码直接逐帧光栅化合成入 4K 画布。
  - 经优化测试，支持导出 **3840×2160 60FPS VP9（50Mbps） + 48kHz Opus 音画同步** 的母带级视频文件。
- **Blender 资产与程序化双引擎容灾**：
  - 支持优先挂载并播放同级目录下的 `zen_core.glb` 3D 模型资产与动画轨道。
  - 若无 GLB 资产，自动优雅降级为电影级程序化三维四幕曼陀罗宇宙。

---

## 🚀 快速启动

本项目为单文件静态架构，无需编译或打包：

```bash
# 本地启动静态服务器（例如使用 Python）
python3 -m http.server 8080

# 在现代浏览器（Chrome / Edge / Safari）中访问
http://localhost:8080
```

1. 点击 **“▶ CLICK TO ENTER VIBE VIDEO (30s)”** 沉浸式观影。
2. 点击右上角 **“🎥 导出 4K 视频”**，将在 30 秒后自动生成并下载 `断舍离_DAN-SHA-RI_4K_UHD_30s.webm`。

---

## 🎞️ 视频转码（WebM 转标准 MP4）

导出的 WebM 文件支持在 Chrome、Edge 和 VLC 播放器中全高清流畅播放。若需导入剪映、Final Cut Pro、PR 或在 Mac QuickTime 中直接打开，可运行以下命令转为高画质 MP4：

```bash
ffmpeg -i 断舍离_DAN-SHA-RI_4K_UHD_30s.webm -c:v libx264 -crf 16 -c:a aac -b:a 320k 断舍离_4K.mp4
```

---

## ☁️ 一键部署到 Cloudflare Pages

本项目无任何后端依赖，非常适合部署在全球边缘 CDN 上：

1. 打开 [Cloudflare Dashboard](https://dash.cloudflare.com/) ➔ 进入 **Workers & Pages** ➔ **Pages**。
2. 选择 **Upload assets**（上传静态资源）。
3. 将包含 `index.html` 的目录拖拽上传即可完成部署。

---

## 🛠️ 技术栈

- **渲染引擎**：[Three.js](https://threejs.org/) (r128)
- **后期处理**：EffectComposer, RenderPass, UnrealBloomPass, ShaderPass
- **音频引擎**：Web Audio API (Oscillators, BiquadFilters, Convolver/Reverb, DynamicGain)
- **视频录制**：HTML5 Canvas API, MediaStream Recording API (VP9, Opus)
