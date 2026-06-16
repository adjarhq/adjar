<div align="center">
  <a href="https://www.adjar.ai">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="assets/adjar-logo-on-dark.svg">
      <img src="assets/adjar-logo-on-light.svg" alt="Adjar" width="172" height="56">
    </picture>
  </a>

  <h3>Google Ads for AI agents.</h3>

  <p>
    <a href="https://www.adjar.ai">Website</a> ·
    <a href="https://www.adjar.ai/docs">Docs</a> ·
    <a href="https://github.com/adjarhq/adjar/issues">Issues</a>
  </p>
</div>

---

Adjar is the Google Ads control layer for AI agents. Instead of clicking
through the Google Ads console, your entire account — campaigns, ad groups,
keywords, budgets, creatives — becomes plain-text TOML config that lives
alongside your code. Your AI agent reads the daily performance reports, drafts
changes as diffs, and you review every one before the `adjar` CLI applies it to
your live account.

- **Your whole account as plain-text config** — TOML files your agents (and
  you) can read, diff, version-control, and edit.
- **Agents draft, you review the diff** — nothing touches your account until
  you approve the change.
- **Applied safely, fully auditable** — every change is a commit; rollback is a
  `git revert`, not a hunt through console history.

## Get started

Install the `adjar` CLI (macOS, Apple silicon + Intel):

```bash
curl -fsSL https://adjar.ai/install.sh | bash
```

This downloads the standalone `adjar` binary, verifies its checksum, and
installs it to `~/.local/bin` — no Node or other runtime required. See the
[quick start](https://www.adjar.ai/docs/quickstart#install-the-cli) for full
setup steps.

## The loop

Adjar replaces the console with a four-step loop your agent can participate in:

1. **Ask** — Tell your agent what you want in plain language. It reads your
   config and the latest reports, then edits the TOML.
2. **Review** — Run `adjar plan` to see every change as a clear diff before
   anything goes live.
3. **Apply** — Approve and run `adjar apply`. Changes ship to Google Ads and
   assigned IDs are written back into your config.
4. **Measure** — Fresh performance data lands in your repo as a daily Markdown
   report, feeding the next round.

```bash
# Export your live account into version-controlled TOML
adjar import --account <account-id> -o config/google.toml

# Ask your agent to make a change, then review the diff
adjar plan --config config/google.toml

# Approve and ship — fully reversible
adjar apply --config config/google.toml
```

Learn more in the [docs](https://www.adjar.ai/docs).

## Bug reports & feature requests

This is Adjar's public issue tracker. If you've hit a bug or want to see
something added, [open an issue](https://github.com/adjarhq/adjar/issues/new) —
we read all of them.

For anything account-specific or private, [contact us](https://www.adjar.ai/contact-us)
instead.
