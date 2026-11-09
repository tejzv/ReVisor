# ReVisor

ReVisor is a high-speed, request-based visual intelligence engine with CLI and API support.
Powered by Google Lens, it brings together OCR, translation, visual recognition, and contextual insights in a streamlined workflow — all with zero disk writes.

## Features

- High-speed visual entity recognition and OCR text extraction (That's why less ai overview for now)
- Fully request-based architecture with connection pooling
- Fast single image, directory bulk processing, and web/URL scraping
- Rest Api Server hosting supported
- Native Windows standalone bootstrap executable (`revisor.exe`)

## Standalone Windows Executable (revisor.exe)

Run `revisor.exe` directly on any Windows system.
automatically setup & launch revisor.

```bash
revisor.exe img/test.png
revisor.exe img/test2.png -t es -y
revisor.exe img/test.png --json
revisor.exe --api
```

## Installation

```bash
pip install -r requirements.txt
```

## CLI Usage

Run OCR with auto language detection:
```bash
python revisor.py img/test.png
```

Translate text into another language (e.g. Spanish):
```bash
python revisor.py img/test2.png -t es -y
```

Draw translation overlay onto the image:
```bash
python revisor.py img/test2.png -t es -to translated_image.png -y
```

Output machine-readable JSON:
```bash
python revisor.py img/test.png --json
```

Batch analyze a folder of images:
```bash
python revisor.py img/ -y
```

Scrape and analyze an image URL:
```bash
python revisor.py https://example.com/image.png -y
```

Launch Api Server:
```bash
python revisor.py --api
```

Interactive mode:
```bash
python revisor.py
```

## Api Server

Start the API server:
```bash
python api.py
```

Or with Uvicorn:
```bash
uvicorn api:app --host 0.0.0.0 --port 8000
```

Available Endpoints:
- `GET /` - Service status and capabilities
- `GET /health` - Health check endpoint
- `POST /search/image` - Analyze uploaded image
- `POST /search/url` - Analyze image URL or web page
- `POST /bulk/image` - Batch analyze uploaded images
- `POST /bulk/url` - Batch analyze list of URLs
- `POST /bulk/url/file` - Batch analyze URLs from uploaded text file
- `POST /task/create` - Asynchronous analysis job
- `GET /task/{task_id}` - Retrieve asynchronous job result

## Python API

```python
import asyncio
from revisor import ReVisor

async def main():
    client = ReVisor()
    result = await client.search("img/test.png")
    print("OCR:", result.get("ocr_text"))
    print("Overview:", result.get("ai_overview"))
    print("Entities:", result.get("detected_entities"))

asyncio.run(main())
```

# Support
- https://discord.gg/PYfeSaDGPJ

## Buy Me A Coffee ☕?
~ **Wallet Address:**
- ltc: LbDG5BE3foVsfK6JRsSc7UtBVX4DqYYKXN

**Make With ♥️ & By Tej**