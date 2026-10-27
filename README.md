# Cho Coder — CLI Tool for AI Security Testing & Computer Tasks

A terminal AI assistant powered by the **DeepSeek API**. It can run shell commands, read and
write files, search the web, fetch pages, and take screenshots — handy for **security testing on
systems you own** and for everyday computer/coding tasks. **Bring your own DeepSeek API key.**

## The whole program is ONE file

The entire tool is a single Python file: **`choshare.py`** (same file for every platform).
`choshare` / `choshare.bat` are just one-line launchers. There is **no other source code.**

## What you need

| Requirement | Notes |
|---|---|
| **Python 3.8+** | **Not built in on macOS or Windows — you must install it** (see per-platform README). Most Linux has it. |
| **A DeepSeek API key** | Get one at https://platform.deepseek.com (uses your DeepSeek credits). Set it with `/key`. |
| **Internet connection** | The model runs in DeepSeek's cloud. |
| *prompt_toolkit* (optional) | `pip install --user prompt_toolkit` — gives the pinned bottom input box. Works without it. |

**No other Python packages are required** — everything else is the Python standard library.

## Builds

| Folder | Platform | Run |
|---|---|---|
| [`mac/`](mac/) | macOS & Linux | `python3 choshare.py` (or `./choshare`) |
| [`windows/`](windows/) | Windows | `python choshare.py` (or double-click `choshare.bat`) |

Each folder's README has step-by-step setup including **how to install Python**.

## Quick start

1. Install **Python 3** (see your platform's README — macOS/Windows do NOT include it).
2. Run `choshare.py`.
3. Inside the app: `/key sk-...` to set your DeepSeek key.
4. Ask anything, or type `/help`. Switch model with `/dsmodel`.

## Features

- **Agentic tools** — the model actually runs `run_command`, `read_file`, `write_file`,
  `take_screenshot`, `web_search`, `fetch_url` on your machine.
- **Two models** — `deepseek-flash` (DeepSeek V4.1 Flash, fast, default) and `deepseek-v4-pro`
  (heavier). Switch with `/dsmodel`.
- **Live input box** — with `prompt_toolkit`, the input stays pinned at the bottom while work runs;
  type to queue a follow-up, `/stop` to interrupt.
- **Max reasoning** on every call, Korean/English UI, a built-in calculator, shell passthrough.

## ⚠️ Safety

- **Auto-run is ON by default** — the model runs shell commands **without asking** (including
  internet commands). A red warning shows at startup. Run with `--safe` to approve each tool.
- **Only use this on machines and networks you own or are authorized to test.**
- Web content is treated as **data, not instructions**.
- Your key/settings live only in `~/.choshare.json` on your own computer — **never in this repo.**

## License

MIT — see [LICENSE](LICENSE).
