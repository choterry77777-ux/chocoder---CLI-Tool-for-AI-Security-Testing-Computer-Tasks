# Cho Coder — Share Edition (Windows)

A terminal AI coding & security-testing assistant powered by the **DeepSeek API**.
The whole program is **one file: `choshare.py`** (no other source, no required pip packages).
Bring your own key. No local model.

## What you need

1. **Python 3.8+** — **Windows does NOT come with Python.** Install it from
   https://www.python.org/downloads/ and **check "Add python.exe to PATH"** in the installer.
   Check it worked (in Command Prompt):
   ```bat
   python --version
   ```
2. **A DeepSeek API key** — get one at https://platform.deepseek.com (uses your DeepSeek credits).
3. *(recommended)* **prompt_toolkit** — pins the input box at the bottom while work runs:
   ```bat
   pip install --user prompt_toolkit
   ```
   Works without it too (simple mode).

That's all — no other Python packages are needed.

## Run

Double-click **`choshare.bat`**, or from Command Prompt / PowerShell:
```bat
python choshare.py
```

> If the window flashes and closes instantly, Python isn't installed or isn't on PATH.
> Open PowerShell, `cd` into this folder, and run `python choshare.py` to see the error.

On first start, set your key inside the app:
```
/key sk-your_key_here
```
(or set the environment variable `DEEPSEEK_API_KEY`)

## Choose / switch the model

Default is **`deepseek-flash`** — DeepSeek **V4.1 Flash** (newest, fast). Recommended for most work.

| Model id | Notes |
|---|---|
| `deepseek-flash` | **Newest V4.1 Flash. Fast, cheap. Default (recommended).** |
| `deepseek-v4-pro` | Larger and slower; thinks deeper on very hard problems. |

```
/dsmodel deepseek-v4-pro      # heavier model
/dsmodel deepseek-flash       # back to the fast default
```

## Input & stop while it's working

- While a task runs, the **input box (❯) stays at the bottom** and a `working (Ns)` indicator shows.
  Type a message + Enter — it **queues** and is sent after the task ends.
- **Stop**: type `/stop` + Enter (stops at the next step) or press **Ctrl-C**.
- Use ↑ / ↓ for previous inputs.

## Commands

```
/help                 this help
/stop                 stop the current task (or Ctrl-C)
/key <KEY>            set your DeepSeek API key
/dsmodel <id>         switch model (deepseek-flash | deepseek-v4-pro)
/think [on|off]       show the model's reasoning
/comp [on|off]        computer control (let the model run tools)
/auto [on|off]        auto-run tools without asking
/web  [on|off]        allow web search / page fetch / internet commands
/lang [en|ko]         interface & reply language
/calc <expression>    calculator  (e.g. /calc (3+4)*2**3)
/graph [clear|save|load]   show the dual-graph (asset + exploration map)
/sh <cmd>  or  !<cmd>  run a shell command directly
/clear                new conversation
/exit                 quit
```

## Dual-Graph (security recon)

For security-testing / recon tasks the model keeps two live graphs and reasons over them each turn:

- **Asset Graph** (`asset_map`) — the target's structure: networks, hosts, services, ports,
  accounts, data.
- **Exploration Graph** (`explore_map`) — likely-vulnerable paths, each finding's status, and the
  next action to take.

You don't drive it — the model builds it as it works. `/graph` shows it; `/graph clear` empties it;
`/graph save [file]` / `/graph load [file]` persist it (default `%USERPROFILE%\.choshare.graph.json`).
Use it only against systems you own or are authorized to test.

## ⚠️ Safety

- **Everything is ON by default**: computer control, web, and **auto-run** — the model runs shell
  commands **without asking**. A red warning appears at startup.
- To approve each tool, start with: `python choshare.py --safe`
- Only run this on machines/networks you own or are authorized to test.
- Your key and settings are stored only in `%USERPROFILE%\.choshare.json` on your computer.
