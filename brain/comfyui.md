# comfyui

local instance at `localhost:8188`. used for image generation.

## available models
- `oneObsession_17RED.safetensors` — semi-realistic anime style. cfg 2.3, 20 steps is enough.
- `novaCrossXL_ilVC.safetensors` — more anime/illustrative style ("brat model"). cfg 7.5 first pass, 5.5 second. uses two-pass workflow: generate → upscale 1.25x lanczos → re-denoise at 0.75.

## api usage

queue a generation:
```
POST http://localhost:8188/prompt
Content-Type: application/json
body: { "prompt": { ... workflow nodes ... } }
```

check result:
```
GET http://localhost:8188/history/<prompt_id>
```
outputs are in `outputs["9"]["images"][0]["filename"]`

download image:
```
GET http://localhost:8188/view?filename=<filename>
```

## tips from pterror
- 20 steps is enough for most generations
- use danbooru tags for prompts (these models are trained on danbooru data)
- extract workflows from example images with `nix run nixpkgs#exiftool -- -Prompt <image.png>`
- example images with embedded workflows: `/home/me/0QynU.png` (semi-realistic), `/home/me/SbGGi.png` (brat)
- standard size: 832x1216
- lots of reference images with prompts at `/mnt/usb/ai/sd/stable-diffusion-webui/output/`
- danbooru tag autocomplete data at `/home/me/.config/comfy-ui/custom_nodes/ComfyUI-Autocomplete-Plus/data/danbooru_tags_cooccurrence.csv` (~100MB, be careful)

## file hosting

sillie.st file uploader for hosting images (greeting images, etc.):
```
PUT https://api.sillie.st/files
Authorization: Bearer <key>
Body: raw file bytes
Response: URL (plain text)
```
key is in pterror's discord DMs (forwarded message). returns a URL like `https://files.sillie.st/<id>.png`.

## ST PNG card format

SillyTavern character cards are PNGs with character data embedded in a `Chara` tEXt chunk (base64-encoded JSON).
- use `nix run nixpkgs#exiftool -- -Chara="$(cat data.b64)" card.png` to embed
- JSON format: v1 fields at top level + `data` field with v3 fields + `spec: "chara_card_v3"`, `spec_version: "3.0"`
- greeting images: markdown image links to sillie.st URLs in `first_mes` / `alternate_greetings`
- example card with metadata: `/home/me/Eve_brat_v1.png`
