# TRELLIS.2 Colab Gradio Notebook

Run the official [microsoft/TRELLIS.2](https://github.com/microsoft/TRELLIS.2) Gradio demo on Google Colab with a GPU runtime.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/GialloInteractive/trellis2-colab-gradio/blob/main/TRELLIS2_Gradio_Colab_EN.ipynb)

## What This Repository Contains

- `TRELLIS2_Gradio_Colab_EN.ipynb`: English Colab notebook for launching TRELLIS.2 with Gradio.
- `SECURITY.md`: Safe sharing and token-handling guidance.
- `NOTICE.md`: Attribution and upstream licensing notes.

This repository does not redistribute TRELLIS.2 source code, model weights, Hugging Face tokens, or generated assets. The notebook clones the official upstream repository at runtime.

## Requirements

- Google Colab with a GPU runtime.
- NVIDIA GPU with at least 24 GB VRAM recommended.
- Hugging Face account.
- Approved access to the gated model `facebook/dinov3-vitl16-pretrain-lvd1689m`.
- A Hugging Face `Read` token stored as a Colab secret named `HF_TOKEN`.

The official TRELLIS.2 README states that the code is tested on Linux with A100/H100 GPUs and recommends CUDA Toolkit 12.4. Colab availability varies by account and plan.

## Quick Start

1. Open `TRELLIS2_Gradio_Colab_EN.ipynb` in Colab.
2. Select `Runtime > Change runtime type > GPU`.
3. Request or accept access to [facebook/dinov3-vitl16-pretrain-lvd1689m](https://huggingface.co/facebook/dinov3-vitl16-pretrain-lvd1689m).
4. Create a Hugging Face token with `Read` permission.
5. Add it to Colab Secrets as `HF_TOKEN` and enable notebook access.
6. Run the notebook cells in order.
7. Open the temporary `gradio.live` link printed by the final cell.

## Important Security Notes

- Never paste Hugging Face tokens directly into notebook cells.
- Do not publish notebook outputs that include logs, usernames, local paths, temporary Gradio links, or errors containing private context.
- Use Colab Secrets for `HF_TOKEN`.
- Treat `gradio.live` links as public temporary links. Anyone with the URL can access the running demo while your session is active.
- For a stable public demo, prefer a dedicated Hugging Face Space with Secrets configured in the Space settings.

## Recommended Public Distribution

For a professional public release:

1. Publish this repository on GitHub.
2. Keep notebooks free of execution outputs.
3. Add a clear Colab badge in this README.
4. Pin important versions when stability matters.
5. Document gated model access and GPU requirements upfront.
6. Use Hugging Face Spaces for a hosted public Gradio app rather than relying on Colab `gradio.live` links.

## Troubleshooting

### `403 Forbidden` for DINOv3

Your Hugging Face account is missing approved access to `facebook/dinov3-vitl16-pretrain-lvd1689m`, or `HF_TOKEN` is missing/incorrect.

### `No module named 'flash_attn'`

Run the backend verification cell. The notebook falls back to `xformers` and launches the app with:

```bash
ATTN_BACKEND=xformers SPARSE_ATTN_BACKEND=xformers python app.py
```

### CUDA out of memory

Start with resolution `512`, lower texture size to `1024` or `2048`, and use a runtime with more VRAM when available.

## Attribution

TRELLIS.2 is developed by Microsoft and released under the MIT License. See:

- [microsoft/TRELLIS.2](https://github.com/microsoft/TRELLIS.2)
- [TRELLIS.2-4B on Hugging Face](https://huggingface.co/microsoft/TRELLIS.2-4B)

If you use TRELLIS.2 in research, cite the upstream project as described in its official README.
