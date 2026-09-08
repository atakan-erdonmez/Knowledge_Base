`source`

The `source` command (or its POSIX-compliant alias `.`) executes a shell script within the **current shell process** rather than creating a new subshell.

Normally, running a script with `./script.sh` creates a child process (a subshell). Any environment variables, aliases, or shell functions set inside that script vanish as soon as the script finishes running.

When you use `source`, the commands run as if you typed them directly into your terminal, allowing changes to persist in your current session.

### Key Behavioral Differences

|**Execution Method**|**Shell Context**|**Variable & Alias Changes**|
|---|---|---|
|`./script.sh` or `bash script.sh`|**New child process (subshell)**|Lost when script finishes|
|`source script.sh` or `. script.sh`|**Current shell process**|Persist in active session|

### Common Use Cases

- **Applying Profile Changes Immediately:**

After updating configuration files like `~/.bashrc`, `~/.zshrc`, or `~/.profile`, reload them without closing the terminal:

```
source ~/.bashrc
```

- **Activating Python Virtual Environments:**

Virtual environments modify path variables and prompt definitions in your current session:

```
source venv/bin/activate
```

- **Loading Modular Functions or Variable Files:**

Import reusable functions or global environment variables into another script:
```
source /path/to/env_variables.env
```