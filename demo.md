# Hello Python — A Showboating Demo

*2026-03-05T14:35:33Z by Showboat 0.6.1*
<!-- showboat-id: 08a3e1d2-9cfa-471c-b5d1-5c2e239ea8dc -->

## What is this?

`hello-python` is a simple Python script that prints a colourful greeting to the terminal using ANSI escape codes and ASCII art. This demo walks through the project: its contents, how to run it, and what the output looks like.

## Project structure

Let's see what's in the repo.

```bash
ls -1 /tmp/hello-python
```

```output
README.md
demo.md
hello.py
```

## The script

Here is the full source of `hello.py`:

```bash
cat /tmp/hello-python/hello.py
```

```output
#!/usr/bin/env python3
"""Hello, World! — with showboating flair."""

RESET  = "\033[0m"
BOLD   = "\033[1m"
RED    = "\033[31m"
YELLOW = "\033[33m"
GREEN  = "\033[32m"
CYAN   = "\033[36m"
MAGENTA= "\033[35m"

banner = f"""
{CYAN}{BOLD}
  ██╗  ██╗███████╗██╗     ██╗      ██████╗
  ██║  ██║██╔════╝██║     ██║     ██╔═══██╗
  ███████║█████╗  ██║     ██║     ██║   ██║
  ██╔══██║██╔══╝  ██║     ██║     ██║   ██║
  ██║  ██║███████╗███████╗███████╗╚██████╔╝
  ╚═╝  ╚═╝╚══════╝╚══════╝╚══════╝ ╚═════╝
{RESET}"""

tagline = (
    f"  {YELLOW}✨ {BOLD}Hello, World!{RESET}{YELLOW} ✨{RESET}\n"
    f"  {GREEN}Greetings from b4-dev — Python never looked this good.{RESET}\n"
    f"  {MAGENTA}~ crafted with pride, deployed with flair ~{RESET}\n"
)

print(banner)
print(tagline)
```

## Running it

Execute the script — output includes ANSI codes (renders as colour in a real terminal):

```python3

import subprocess, sys
result = subprocess.run(['python3', '/tmp/hello-python/hello.py'], capture_output=True, text=True)
# Strip ANSI for clean demo output
import re
clean = re.sub(r'\x1b\[[0-9;]*m', '', result.stdout)
print(clean.strip())

```

```output
██╗  ██╗███████╗██╗     ██╗      ██████╗
  ██║  ██║██╔════╝██║     ██║     ██╔═══██╗
  ███████║█████╗  ██║     ██║     ██║   ██║
  ██╔══██║██╔══╝  ██║     ██║     ██║   ██║
  ██║  ██║███████╗███████╗███████╗╚██████╔╝
  ╚═╝  ╚═╝╚══════╝╚══════╝╚══════╝ ╚═════╝

  ✨ Hello, World! ✨
  Greetings from b4-dev — Python never looked this good.
  ~ crafted with pride, deployed with flair ~
```

## Verify it works

`showboat verify` re-runs every code block and confirms the output still matches — making this document a living proof of work.
