# Google AI Edge Gallery — Snapdragon/Android 11 compatibility build

This repository is a clean public source snapshot with the compatibility changes applied directly on the default branch.

Applied changes:

- Android minimum SDK raised to API 30 for Android 11 testing.
- Safe `SOC_MODEL` lookup without a direct API 31 field reference, with Android 11 fallback values.
- Bundled model allowlist for Gallery 1.0.20 under `Android/src/app/src/main/assets/model_allowlists/1_0_20.json`.
- Bundled allowlist is preferred before the remote GitHub allowlist, so corrected model revisions remain usable when the remote file is stale or unavailable.
- Model revisions were audited against the current Hugging Face repositories. HTTP 401 responses indicate gated models requiring Hugging Face authentication; they are not broken 404 links.

The source remains based on the official Google AI Edge Gallery project. See `RELATORIO_AUDITORIA_DOWNLOADS.md` and `RELATORIO_COMPATIBILIDADE_ANDROID11.md` for the validation notes.
