# ClaudeClaw downloads

Public preview installers only. The application source repository remains private.

## macOS Apple Silicon

Requires Node.js 22 or newer. Open Terminal and run:

```sh
npx --yes --package=https://github.com/hoanghd218/claudeclaw-downloads/releases/download/v1.11.0-preview.1/claudeclaw-local-installer-0.2.0.tgz claudeclaw-install
```

The command opens the local installation page. Click Install, configure your own
AI account and Telegram bot, save configuration, then start and open the dashboard.
Keep Terminal open while using the installer. Application data is stored outside
the npm cache, under `~/Library/Application Support/ClaudeClaw` by default.

To test alongside an existing installation, use a separate data directory:

```sh
npx --yes --package=https://github.com/hoanghd218/claudeclaw-downloads/releases/download/v1.11.0-preview.1/claudeclaw-local-installer-0.2.0.tgz claudeclaw-install --home "$HOME/ClaudeClaw-Pilot"
```

Use a separate Telegram bot and dashboard port such as 32550. Use the same `--home`
when opening this test instance again.

To download and install the runtime directly before opening setup:

```sh
npx --yes --package=https://github.com/hoanghd218/claudeclaw-downloads/releases/download/v1.11.0-preview.1/claudeclaw-local-installer-0.2.0.tgz claudeclaw-install install
```

## Preview limitations

- Only macOS arm64 / Apple Silicon has a runtime in this preview. Windows is pending.
- Application version 1.11.0, npm bootstrap version 0.2.0.
- Runtime packages are signed; the public key is bundled in the npm bootstrap.
- Application JavaScript is obfuscated, but can still be reverse engineered.
- No license activation or per-machine restrictions.
- No customer AI/Telegram end-to-end certification, automatic login startup,
  bundled personal skills, voice/Python, War Room or WhatsApp browser.
- This preview is for a new pilot installation. Do not use it to update an existing
  customer deployment without checking its pinned signing key and application version.

No private signing keys, developer credentials, customer data, or original
application TypeScript source are included in this repository or the release assets.
