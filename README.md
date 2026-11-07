# Vigil for Scoop

The Scoop bucket for [Vigil](https://github.com/godspeedhq/vigil), a job scheduler, supervisor and metrics forwarder written only in the shells that ship with each OS. Windows.

```powershell
scoop bucket add vigil https://github.com/godspeedhq/scoop-vigil
scoop install vigil
vigil service install --user     # starts it at every logon
```

- Your configuration, scripts, state and logs are in `~\scoop\persist\vigil`. `vigil config` edits the configuration; `vigil status` shows what it is doing.
- `scoop update vigil` updates it: a running supervisor picks up the new version by itself.
- `scoop uninstall vigil` removes the program and its logon entry and keeps `~\scoop\persist\vigil`; `scoop uninstall -p vigil` removes that too.
- For a service that runs without anyone logged on, use Vigil's installer instead: see its README.

## How the manifest is made

`bucket/vigil.json` is written by Vigil's own `tools/release/tap-bucket.sh` from each release, with the archive's hash from the release's `SHA256SUMS`. The `update` workflow checks for a new release every hour, verifies `SHA256SUMS` against `release-key.pem` here, and commits the new manifest. Change the manifest in the Vigil repository (`packaging/scoop/vigil.json.in`), not here.

Licensed under the Apache License 2.0.
