# Codex Bridge Scoop Bucket

A community-maintained Scoop manifest for the official [Codex Bridge](https://github.com/Fanch-hui/codex-bridge) Windows portable release. Not affiliated with the upstream project or ScoopInstaller.

## Install

```powershell
scoop bucket add bridge https://github.com/silencestarrystarry/test
scoop install bridge/codex-bridge
```

If a local `codex-bridge.json` was installed previously, first exit the app, back up its settings, uninstall the old entry, then install `bridge/codex-bridge`.

## Update

```powershell
scoop update
scoop update codex-bridge
```

Exit Codex Bridge fully before updating. Scoop's local update runs only when invoked; GitHub Actions updates this repository's manifest every six hours when the upstream stable release changes.

## Automation

- `bucket/codex-bridge.json`: Windows x64 and ARM64 portable ZIP manifest
- `.github/workflows/excavator.yml`: [ScoopInstaller/GithubActions](https://github.com/ScoopInstaller/GithubActions) checks new releases and updates SHA256
- `.github/workflows/validate.yml`: checks manifest structure
- `scripts/validate_manifest.py`: local structural validation

To allow the updater to commit, enable **Settings → Actions → General → Workflow permissions → Read and write permissions** and permit third-party Actions if necessary. Run **Actions → Update Scoop manifests → Run workflow** to verify it. The workflow declares `contents: write` and uses GitHub's automatic `GITHUB_TOKEN`; no PAT is needed.

The upstream archive is not bundled here. Download URLs and hashes are sourced from GitHub Releases. Installation has not been tested on Windows in this environment.

> This bucket is currently hosted in the existing `test` repository. You can rename it to `scoop-codex-bridge` in GitHub Settings → General without rebuilding the manifest; use the new URL when adding the bucket to new machines.
