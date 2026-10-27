# Cho Coder — CLI Tool for AI Security Testing & Computer Tasks

A terminal AI assistant powered by the **DeepSeek API**. It can run shell commands, read and
write files, search the web, fetch pages, and take screenshots — handy for **security testing on
systems you own** and for everyday computer/coding tasks. **Bring your own DeepSeek API key.**

It runs as a single Python file. No local model, no account — 100% API.

## Builds

| Folder | Platform | Launcher |
|---|---|---|
| [`mac/`](mac/) | macOS & Linux | `python3 choshare.py` (or `./choshare`) |
| [`windows/`](windows/) | Windows | `python choshare.py` (or `choshare.bat`) |

Each folder has its own README with full instructions.

## Quick start

1. Install **Python 3** (and optionally `prompt_toolkit` for the pinned input box).
2. Run `choshare.py` for your platform.
3. Set your key inside the app: `/key sk-...`
4. Ask anything, or try `/help`.

## Features

- **Agentic tools** — the model actually runs `run_command`, `read_file`, `write_file`,
  `take_screenshot`, `web_search`, `fetch_url` on your machine.
- **Two models** — `deepseek-flash` (DeepSeek V4.1 Flash, fast, default) and `deepseek-v4-pro`
  (heavier). Switch with `/dsmodel`.
- **Live input box** — with `prompt_toolkit`, the input stays pinned at the bottom while work runs;
  type to queue a follow-up, `/stop` to interrupt.
- **Max reasoning** on every call, Korean/English UI, a built-in calculator, and shell passthrough.

## ⚠️ Safety

- **Auto-run is ON by default** — the model runs shell commands **without asking** (including
  internet commands). A red warning shows at startup. Run with `--safe` to approve each tool.
- **Only use this on machines and networks you own or are authorized to test.** You are responsible
  for what you run.
- Content fetched from the web is treated as **data, not instructions**.
- Your key and settings live only in `~/.choshare.json` on your own computer (never in this repo).

## License

MIT — do what you want, no warranty.
