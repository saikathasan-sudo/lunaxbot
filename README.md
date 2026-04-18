# LunaxBot Releases

Official Windows installer release repository for LunaxBot.

## Install (PowerShell, one line)

```powershell
irm https://lunaxbot.vercel.app/install | iex
```

The installer script is served from `https://lunaxbot.vercel.app/install` and will:

1. Show source URL, destination path, and a trust warning
2. Ask for explicit user confirmation
3. Download `LunaxBotSetup.exe`
4. Download `LunaxBotSetup.exe.sha256`
5. Verify checksum before execution
6. Run normal visible installer UI
7. Launch app after setup

## Release assets required

Every release must include both files:

- `LunaxBotSetup.exe`
- `LunaxBotSetup.exe.sha256`

Checksum generation:

```powershell
Get-FileHash .\release\LunaxBotSetup.exe -Algorithm SHA256 | ForEach-Object { "$($_.Hash)  LunaxBotSetup.exe" } | Out-File -Encoding ascii .\release\LunaxBotSetup.exe.sha256
```

## Repositories

- Web/backend source (Vercel): [`saikathasan-sudo/lunaxbot-web`](https://github.com/saikathasan-sudo/lunaxbot-web)
- Release assets: [`saikathasan-sudo/lunaxbot`](https://github.com/saikathasan-sudo/lunaxbot)

## Security notes

- Installer integrity is enforced with SHA256 verification.
- App package uses ASAR + scoped obfuscation + runtime checks.
- If backend attestation secrets are enabled, non-official patched clients are blocked from config/heartbeat APIs.