# Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/TheBaron13/RBX-Manager.git
   ```
2. Navigate to the project directory:
   ```bash
   cd RBX-Manager
   ```
3. Install the package in development mode with dependencies:
   ```bash
   pip install -e .
   ```

This will install the package and set up the `rbx-m` command for easy access.

## Quick Start

After installation, you can use the tool with the shortened command:

```bash
rbx-m create-db /path/to/output /path/to/music --config /path/to/config.json
```

Instead of:
```bash
python main.py create-db /path/to/output /path/to/music --config /path/to/config.json
```