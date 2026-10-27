# Cho Coder — Share Edition (Windows)

A terminal AI coding & security-testing assistant powered by the **DeepSeek API**.
Just one file (`choshare.py`). Bring your own key. No local model.

## 1. Requirements

- **Python 3** — install from https://python.org and **check "Add Python to PATH"** during setup.
- A **DeepSeek API key** — get one at https://platform.deepseek.com
- *(recommended)* **prompt_toolkit** — keeps the input box pinned at the bottom while work runs:
  ```bat
  pip install --user prompt_toolkit
  ```
  Works without it too (simple mode).

## 2. Run

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

## 3. Choose / switch the model

Default is **`deepseek-flash`** — DeepSeek **V4.1 Flash** (newest, fast). Recommended for most work.

| Model id | Notes |
|---|---|
| `deepseek-flash` | **Newest V4.1 Flash. Fast, cheap. Default (recommended).** |
| `deepseek-v4-pro` | Larger and slower; thinks deeper on very hard problems. |

Switch inside the app:
```
/dsmodel deepseek-v4-pro      # heavier model
/dsmodel deepseek-flash       # back to the fast default
```

## 4. Input & stop while it's working

- While a task runs, the **input box (❯) stays at the bottom** and a `working (Ns)` indicator shows.
  Type a message + Enter — it **queues** and is sent after the task ends.
- **Stop**: type `/stop` + Enter (stops at the next step) or press **Ctrl-C**.
- Use ↑ / ↓ for previous inputs.

## 5. Commands

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
/sh <cmd>  or  !<cmd>  run a shell command directly
/clear                new conversation
/exit                 quit
```

## ⚠️ Safety

- **Everything is ON by default**: computer control, web, and **auto-run** — the model runs shell
  commands **without asking**. A red warning appears at startup.
- To approve each tool, start with: `python choshare.py --safe`
- Only run this on machines/networks you own or are authorized to test.
- Your key and settings are stored only in `%USERPROFILE%\.choshare.json` on your computer.
