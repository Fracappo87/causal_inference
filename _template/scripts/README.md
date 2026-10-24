# Scripts

Only the entry points you actually want to run on their own (e.g. a full simulation study that writes to `results/`).
Reusable code belongs in `src/experiment/`, not here. Run a script with:

```bash
uv run scripts/<name>.py
```
