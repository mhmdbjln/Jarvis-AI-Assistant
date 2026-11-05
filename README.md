# JARVIS — Local macOS AI Desktop Assistant

JARVIS is a personal desktop assistant built with Python. Its current primary language-model workflow uses a locally hosted model through [Ollama](https://ollama.com/), with registered tools for selected macOS operations.

> **Status: Work in progress.** This repository reflects a development snapshot. Some modules are placeholders, and feature availability depends on local dependencies, model availability, permissions, and hardware.

## Current implementation snapshot

- Local LLM integration through the Ollama Python client.
- Text interaction through a command-line entry point and a Tkinter desktop interface.
- SQLite-backed conversation, profile, and reminder storage.
- Registered macOS tools for application control, system information and monitoring, volume, clipboard, and window operations.
- File search and reading, screenshots, OCR, and image analysis through the configured Ollama vision model.
- Web search and URL fetching utilities.
- Voice components for microphone recording, Faster-Whisper transcription, OpenWakeWord detection, and macOS text-to-speech.

The codebase contains additional experimental modules and placeholders. The list above describes components present in this snapshot; it does not claim that every integration has been validated on a clean machine.

## Technology

- Python
- Ollama
- Tkinter and PyObjC
- SQLite
- Faster-Whisper and OpenWakeWord
- NumPy, SoundDevice, and SoundFile
- Requests, Beautiful Soup, and DDGS
- Pillow and pytesseract

## Requirements

- macOS is required for native desktop/menu-bar integration and several system-control tools.
- Python 3.11 or newer is recommended. The project was developed in a Python 3.13 environment; compatibility of audio and ML dependencies may vary by platform.
- Install and run [Ollama](https://ollama.com/).
- Pull the models currently configured in `app/config/settings.py`:

```bash
ollama pull qwen3:8b
ollama pull qwen2.5vl:7b
```

Some features also need system utilities: Tesseract for OCR and PortAudio for microphone audio.

## Installation

```bash
git clone https://github.com/mhmdbjln/Jarvis-AI-Assistant.git
cd Jarvis-AI-Assistant
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install -r requirements.txt
```

On macOS, install optional system utilities when needed:

```bash
brew install tesseract portaudio
```

Start the command-line assistant:

```bash
python run.py
```

Start the desktop interface:

```bash
python -m app.ui.gui
```

The desktop interface and automation features may request macOS privacy permissions. Grant only the permissions required for the features you use.

## Source bundle

The complete application source snapshot is provided as `source-code.tar.xz` in the repository root. After cloning the repository, extract it from the project root:

```bash
tar -xJf source-code.tar.xz
```

This archive contains the `app/` package and `run.py`. It excludes runtime data, local databases, virtual environments, and test files.

## Tests

Automated test files are not included in this source snapshot. The repository should therefore be treated as a development project rather than a tested release.

## Configuration and privacy

- The primary Ollama workflow does not require an API key.
- Do not commit `.env` files, API keys, conversation databases, local memory, logs, or personal data.
- Runtime data and local databases should remain outside version control.
- Do not commit virtual environments, Python bytecode, or macOS metadata files.

## License

No license has been specified. Add one only after deciding how others may use, modify, and distribute this project.
