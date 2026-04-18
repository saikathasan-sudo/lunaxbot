# LunaxBot Release Guide

This repository is used for publishing Windows installer files.

## Required files per release

- `LunaxBotSetup.exe`
- `LunaxBotSetup.exe.sha256`

## How users can install

### Option A: Direct EXE

1. Download `LunaxBotSetup.exe`
2. Double click installer
3. Follow setup UI
4. Launch app

### Option B: PowerShell installer

1. Open PowerShell
2. Run:
   ```powershell
   irm <your-install-endpoint>/install | iex
   ```
3. Confirm Y/N
4. Let installer complete

## Create checksum

```powershell
Get-FileHash .\LunaxBotSetup.exe -Algorithm SHA256 | ForEach-Object { "$($_.Hash)  LunaxBotSetup.exe" } | Out-File -Encoding ascii .\LunaxBotSetup.exe.sha256
```

## SmartScreen

If SmartScreen warning appears:

1. `More info`
2. `Run anyway`
