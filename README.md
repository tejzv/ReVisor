<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,50:161b22,100:1f6feb&height=180&section=header&text=Visor&fontSize=62&fontColor=ffffff&animation=fadeIn&fontAlignY=38&desc=ReVisor%20%E2%80%A2%20Visual%20Intelligence%2C%20OCR%20%26%20Translation%20Engine&descAlignY=62&descSize=17" width="100%" />

[![Python](https://img.shields.io/badge/Python-3.12-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Platform](https://img.shields.io/badge/Windows-Native_Launcher-0078D4?style=for-the-badge&logo=windows&logoColor=white)](#standalone-windows-executable)
[![API](https://img.shields.io/badge/REST_API-Supported-009688?style=for-the-badge&logo=fastapi&logoColor=white)](#rest-api-server)
[![License](https://img.shields.io/badge/License-MIT-238636?style=for-the-badge)](https://github.com/tejzv/ReVisor)

</div>

---

## Overview

**Visor** (**ReVisor**) is a lightweight, unlimited-use, request-based visual intelligence engine combining fast OCR text extraction, multi-language text & in-place image translation, entity recognition, and contextual overview synthesis — with zero browser overhead.

| Capability | Details |
| :--- | :--- |
| **Quick & Detailed Modes** | Run in **Quick** (`-f`, default) for rapid results or **Detailed** (`-d`) for deeper multi-region analysis and rich contextual summaries. |
| **Instant Mode Switching** | Press **`Tab`** or **`M`** inside the interactive terminal UI to toggle `Mode: Quick` ↔ `Mode: Detailed` on the fly. |
| **Text & Image Translation** | Accepts language shortcuts (`en`, `es`, `ja`, `fr`) and full names (`English`, `Spanish`, `Japanese`) across 100+ languages. |
| **Symmetrical `results/` Output** | Automatically saves clean before/after image pairs (`results/before1.png`, `results/result1.png`) and `results/results.txt`. |
| **Batch, URL & REST API** | Process single files, folders, webpage/image URLs, URL lists, or host as a concurrent REST API server. |
| **Zero-Config `.exe`** | Standalone Windows launcher (`revisor.exe`) handles automatic environment setup on first run. |

---

## Standalone Windows Executable

Run `revisor.exe` directly from your terminal with zero manual setup:

```bash
revisor.exe
revisor.exe img/test.png
revisor.exe img/test2.png -d
revisor.exe img/test2.png -t Spanish
revisor.exe img/test2.png -t es -tt
revisor.exe img/test2.png -t fr -ti
revisor.exe img/test.png --json
revisor.exe --api
```

---

## CLI Usage

```bash
# Quick mode (default)
python revisor.py img/test.png

# Detailed mode (deeper visual inspection & extended overview)
python revisor.py img/test2.png -d

# Translate image (saves results/beforeN.png, results/resultN.png & results/results.txt)
python revisor.py img/test2.png -t Spanish

# Text-only translation (results/results.txt) or Image-only translation (results/)
python revisor.py img/test2.png -t es -tt
python revisor.py img/test2.png -t es -ti

# Save translated overlay to a custom file path
python revisor.py img/test2.png -t es -to translated_image.png -y

# Machine-readable JSON output
python revisor.py img/test.png --json
python revisor.py img/test2.png -d --json

# Batch analyze or translate folders & URLs
python revisor.py img/ -y
python revisor.py img/ -t French -y
python revisor.py https://example.com/image.png -y
python revisor.py urls.txt -y

# Launch REST API server or Interactive UI
python revisor.py --api
python revisor.py
```

### Interactive Menu

Press **`Tab`** or **`M`** on the menu to switch between **`Mode: Quick`** and **`Mode: Detailed`** immediately:

```text
1. Bulk Img Vision
2. Bulk Url Vision
3. Bulk Translate Vision       -> 1. Text Translation / 2. Image Translation
4. Single Translate Vision     -> 1. Text Translation / 2. Image Translation
5. Single Img Vision
6. Single Url Vision
7. Launch Api Server
```

---

## REST API Server

Start the API server:

```bash
python api.py
```

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/` | Service status, supported modes, and capabilities |
| `GET` | `/health` | Health check endpoint |
| `POST` | `/search/image` | Analyze uploaded image (`target_lang`, `mode=quick\|detailed`) |
| `POST` | `/search/url` | Analyze public image or webpage URL (`url`, `target_lang`, `mode`) |
| `POST` | `/bulk/image` | Concurrent batch image analysis |
| `POST` | `/bulk/url` | Concurrent batch URL analysis |
| `POST` | `/bulk/url/file` | Concurrent batch URL analysis from uploaded file |
| `POST` | `/task/create` | Create asynchronous analysis job |
| `GET` | `/task/{task_id}` | Poll asynchronous job status & result |

---

## Python API

```python
import asyncio
from revisor import ReVisor

async def main():
    async with ReVisor() as client:
        result = await client.search("img/test2.png", mode="detailed")
        print("Mode:", result.get("mode"))
        print("OCR:", result.get("ocr_text"))
        print("Overview:", result.get("ai_overview"))
        print("Entities:", result.get("detected_entities"))

asyncio.run(main())
```

---

## Support & Contact

- **Discord Server**: https://discord.gg/PYfeSaDGPJ
- **Contact**: [@sqnq](https://discord.com/users/987979957907116052)

### Buy Me A Coffee ☕

**Litecoin (LTC)** — click the copy icon on the right:

```text
LbDG5BE3foVsfK6JRsSc7UtBVX4DqYYKXN
```

<div align="center">

**Made With ♥️ By [Tej](https://github.com/tejzv)**

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,50:161b22,100:1f6feb&height=100&section=footer" width="100%" />

</div>
