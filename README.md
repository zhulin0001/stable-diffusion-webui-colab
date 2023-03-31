## A Stable-Diffusion-WebUI-Colab Modified by me.

| Colab Page | Type | Device
| --- | --- | --- |
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/zhulin0001/stable-diffusion-webui-colab/blob/main/stable_diffusion_webui_colab_by_zl.ipynb) | WebUI | GPU
      
## 🚦 WIP 🚦

### Main Repo
https://github.com/zhulin0001/stable-diffusion-webui-colab

## Intro
由[TASUKU2023](https://twitter.com/TASUKU2023)创建的`chilloutmix`模型因生成亚洲女性的像逼真而美观而备受欢迎。

该模型本身并非免费商用。幸运的是，通过其[配方](https://twitter.com/orange_mixer_y/status/1632319367181656064)，您可以创建自己的模型以避免许可问题。

实际上，`chilloutmix`模型是从几个其他模型合并而来的。

本文将向您展示如何借助[Stable Diffusion Web UI](https://github.com/AUTOMATIC1111/stable-diffusion-webui)帮助合并自己的`chilloutmix`模型。

如果您没有强大的电脑，也可以使用此Colab进行操作。

### 启动您的 `Stable Diffusion Web UI` 并转到 `Checkpoint Merger` 选项卡。

### Step 1: Merge LOFI and Colorful

- Primary model: Lofi
- Secondary model: Colorful
- CustomName: LofiColorfulMix
- Multiplier: 0.5
- Interpolation method: Weighted sum
- Checkpoint format: safetensors
- Bake in VAE: vae-ft-mse-840000-ema-pruned.safetensors

### Step 2: Merge Basil

- Primary model: Basil_mix_fixed
- Secondary model: LofiColorfulMix
- CustomName: BasilLofiColorfulMix
- Multiplier: 0.7
- Interpolation method: Weighted sum
- Checkpoint format: safetensors
- Bake in VAE: vae-ft-mse-840000-ema-pruned.safetensors

### Step 3: Merge Muse V1

- Primary model: museV1_v1
- Secondary model: BasilLofiColorfulMix
- CustomName: chilled_re-generic
- Multiplier: 0.6
- Interpolation method: Weighted sum
- Checkpoint format: safetensors
- Bake in VAE: vae-ft-mse-840000-ema-pruned.safetensors

### Succuss 🎉

现在您已经合并了自己的`chilled_re-generic`模型。

## Reference

- [chilled_re_generic: Merge Your Own Chilloutmix Model](https://atlassc.net/2023/03/12/chilled-re-generic)