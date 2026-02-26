# Rockbox Database Manager

A Python tool to generate and manage the Rockbox music database (`.tcd` files) for your music collection.

## Quick start (short commands)

1. Clone the repository and enter it:
```bash
git clone https://github.com/TheBaron13/RBX-Manager.git
cd RBX-Manager
```

2. (Optional) Create and activate a virtual environment:
```bash
python -m venv .venv
# macOS / Linux
source .venv/bin/activate
# Windows (PowerShell)
.venv\Scripts\Activate.ps1
```

3. Install the package in editable mode so the command-line shortcut is available:
```bash
pip install -e .
```

After step 3 you can run the CLI using the short command:
```bash
rbx-m <command> [options]
```
Example:
```bash
# Create or update a Rockbox database
rbx-m create-db /path/to/output /path/to/music --config config.json --verbose
```

If you prefer not to install, you can still run the script directly:
```bash
python main.py <command> [options]
```

## Why this works

This repository provides a console script entry point. The installation step (`pip install -e .`) installs an executable named `rbx-m` (defined in `pyproject.toml` under `[project.scripts]`) that calls the package's `main()` function. `setup.py` also includes entry points for the same behavior. Installing in editable mode keeps the command linked to your local source so changes take effect immediately.

## Features

- Scans your music directory for supported audio files.
- Extracts metadata and generates Rockbox-compatible database files.
- Caches metadata to speed up runs.
- Interactive CLI with verbose logging and filtering options.
- Configurable tag mappings and default values.

## Requirements

- Python 3.7+
- mutagen (installed automatically if you use the package dependencies)
- tqdm (installed automatically if you use the package dependencies)

## Installation (full)

Option A — Install editable (development) mode (recommended for contributors / local edits):
```bash
pip install -e .
```

Option B — Install dependencies only (run without creating console script):
```bash
pip install -r requirements.txt
```

## Usage (examples)

Both forms work; the first is the short installed command, the second is the direct Python-run fallback.

Create or update database:
```bash
# Short (after pip install -e .)
rbx-m create-db /path/to/output /path/to/music --config /path/to/config.json [--verbose] [--show-songs] [--dry-run]

# Direct (no install)
python main.py create-db /path/to/output /path/to/music --config /path/to/config.json [--verbose] [--show-songs] [--dry-run]
```

Validate:
```bash
rbx-m validate /path/to/output
# or
python main.py validate /path/to/output
```

List tags:
```bash
rbx-m list-tags /path/to/music
# or
python main.py list-tags /path/to/music
```

Sync to device:
```bash
rbx-m sync /path/to/source /path/to/rockbox/device
# or
python main.py sync /path/to/source /path/to/rockbox/device
```

Clear metadata cache:
```bash
rbx-m clear-cache
# or
python main.py clear-cache
```

Show help:
```bash
rbx-m --help
# or
python main.py --help
```

## Configuration

The tool uses a `config.json` file to customize tag mappings and default values. Example:
```json
{
  "mappings": { "grouping": "title" },
  "default_values": {
    "artist": "Unknown Artist",
    "album": "Unknown Album",
    "title": "Unknown Title",
    "albumartist": "Unknown Album Artist"
  },
  "chunk_size": 1000
}
```

## Supported audio formats

- `.mp3`, `.flac`, `.wav`, `.ogg`, `.wma`, `.aac`, `.m4a`, `.alac`, `.aiff`, `.ape`, `.wv`, `.mod`, `.spc`

## License

This project is licensed under the MIT License.
