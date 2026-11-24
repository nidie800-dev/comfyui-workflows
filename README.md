# ComfyUI Workflows

一组在 **ComfyUI 0.39.0**（Windows portable，RTX 5060 Laptop 8GB，`LOW_VRAM`）上实际跑通的 Qwen-Image 2.1 与 MiniMax H3 工作流，按图片 / 视频分类整理。

工作流结构来自 ComfyUI 官方模板，本仓库的增量主要是：**中文 prompt 预设、参数与镜头拆分、显存受限下的可用配置**。不包含任何模型权重。

## 目录

```text
workflows/
├── image_qwen_image_2_1_t2i.json                  # Qwen-Image 2.1 文生图
├── image_qwen_image_2_1_turbo_t2i.json            # Qwen-Image 2.1 Turbo 文生图（少步数）
├── image_qwen_image_2_1_image_edit.json           # Qwen-Image 2.1 图像编辑
├── image_qwen_image_2_1_turbo_image_edit.json     # Qwen-Image 2.1 Turbo 图像编辑
├── QwenEdit_单图_明亮清晰_MG09.json                # 单图编辑：提亮、去灰、增强细节
├── QwenEdit_单图_重打光_明亮.json                  # 单图编辑：重新打光
├── QwenEdit_单图_风格统一_MG09.json                # 单图编辑：统一风格/色调
├── video_minimax_h3_i2v.json                      # MiniMax H3 图生视频
├── video_minimax_h3_r2v_image_plus_video.json     # MiniMax H3 参考图 + 参考视频
├── MiniMaxH3_首尾帧_FLF2V_16比9.json              # 首帧 + 尾帧转视频，16:9
├── MiniMaxH3_多图长镜头_3关键帧_16比9.json         # 3 关键帧长镜头，16:9
├── MiniMaxH3_风_MG01_乡间小路_480p.json            # 风景镜头 480p
├── MiniMaxH3_风_MG02_樱花小路_480p.json            # 风景镜头 480p
└── MiniMaxH3_风_MG03_水田草丛_480p.json            # 风景镜头 480p
```

## 使用方法

1. ComfyUI 里直接把 `.json` 拖进画布，或菜单 `Workflow → Open`。
2. 首次打开会提示缺少节点/模型，按提示安装（全部为 ComfyUI 内置或官方模板节点，无需第三方插件）。
3. 在 `LoadImage` / `LoadVideo` 里换成自己的素材；prompt 节点里替换成自己的描述。
4. Qwen 系列工作流内的 Note 节点附有官方模型下载地址。

## 模型依赖

| 系列 | 模型 | 来源 |
|---|---|---|
| Qwen-Image 2.1 | `qwen_image_2.1_int8_convrot`、`qwen_image_2.1_turbo_int8_convrot`、`qwen3vl_8b_int8_convrot`、`qwen3.5_9b_qwen_image_2.1_pe_t2i / pe_i2i`、`qwen_image_2.1_vae_bf16` | [Comfy-Org/Qwen-Image-2.1](https://huggingface.co/Comfy-Org/Qwen-Image-2.1) |
| MiniMax H3 | `minimax_h3_fl2va_pruned`、`minimax_h3_ref2va_pruned`、`qwen3vl_32b_minimax_h3_nvfp4_awq`、`minimax_h3_video_vae_int8_convrot`、`minimax_h3_audio_vae_fp32` 及 4step / 8step turbo LoRA | ComfyUI 官方 MiniMax H3 模板内的下载说明 |

模型权重不在本仓库，使用时请遵守各模型自己的许可证。

## 显存与速度

- 以上配置在 **8GB 显存** 笔记本上以 `--lowvram` 运行；H3 视频建议先按 480p / 短时长跑通，再逐步加长。
- Qwen-Image Turbo 系列步数少，适合先出构图，再用标准版细化。

## 来源与声明

- 工作流骨架来自 **ComfyUI 官方 workflow templates**（`comfyui-workflow-templates`），版权归 Comfy 组织及其贡献者所有。
- 本仓库只声明对 **prompt 预设、参数组合、镜头拆分** 等调整部分的改动，不对官方模板本身主张原创。
- 本仓库仅收录通用、非成人向的工作流，未包含任何 NSFW 内容。
- 仓库内不含模型权重、不含生成素材、不含 API Key。

## 相关项目

- [EmoCue](https://github.com/nidie800-dev/emotion-tts-cue)：把带情感标签的剧本变成分段 TTS + Cue 表 + Cubase 时间线标记。
