# Writ

**Your configuration, inscribed. Ready on first login.**

Writ manages dotfiles and user configuration across machines. Declare your configuration once — writ deploys it everywhere you work.

## Philosophy

**Dotfiles without the friction.**

Every developer has dotfiles. Most sync them via git and symlinks. Writ takes this further: platform-aware configuration, secure secrets handling, and seamless integration with [lore](https://github.com/NobleFactor/lore) for complete machine setup.

**Declare once, deploy anywhere.**

```bash
writ deploy
```

Your shell configs, editor settings, and tool preferences — deployed to any machine. Darwin, Linux, or Windows. Writ adapts paths and formats as needed.

**Secrets stay secret.**

Configuration often includes sensitive data: API tokens, SSH keys, credentials. Writ integrates with your secrets manager (1Password, Bitwarden, system keychain) so secrets never touch your git repo.

## How It Works

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  User Configuration Repository                                              │
│  ~/.config/writ/ or dedicated repo                                          │
│                                                                              │
│  ├── configs/                                                               │
│  │   ├── all/           # All platforms                                     │
│  │   ├── darwin/        # macOS-specific                                    │
│  │   ├── linux/         # Linux-specific                                    │
│  │   └── windows/       # Windows-specific                                  │
│  ├── secrets.yaml       # Secret references (not values)                    │
│  └── writ.yaml          # Deployment configuration                         │
└─────────────────────────────────────────────────────────────────────────────┘
                                  │
                                  ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│  Writ Deploy                                                                 │
│  - Detects platform                                                         │
│  - Resolves config hierarchy (all → platform-specific)                      │
│  - Fetches secrets from configured provider                                 │
│  - Symlinks or copies files to target locations                             │
└─────────────────────────────────────────────────────────────────────────────┘
                                  │
                                  ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│  Deployed Configuration                                                     │
│  ~/.bashrc → configs/all/.bashrc                                            │
│  ~/.config/git/config → configs/all/.config/git/config                      │
│  ~/.ssh/config → generated from template + secrets                          │
└─────────────────────────────────────────────────────────────────────────────┘
```

## CLI

```bash
# Deploy configuration to current machine
writ deploy

# Deploy specific config group
writ deploy shell git

# Show what would be deployed (dry run)
writ deploy --dry-run

# Check configuration status
writ status

# Initialize writ in a repo
writ init
```

## Lore + Writ

**Feel at home anywhere, ready to work from the first login.**

Use **[lore](https://github.com/NobleFactor/lore)** to manage packages and build out development environments. Use **writ** to deploy your personal configuration. Together, they give you a complete, reproducible setup on any machine.

- **Lore** — Tribal knowledge about installing software. The wisdom.
- **Writ** — Your configuration, inscribed. The written form.

Together: knowledge and its application. What you know, and how you've written it down.

## Status

Writ is currently in the design phase. See the [design document](https://github.com/David-Noble-at-work/personal/blob/develop/design/writ-design.md) for detailed architecture and roadmap.

## License

MIT License. See [LICENSE](LICENSE) for details.
