# ot-mb-test

Scratch repo — holds only a GitHub Actions workflow, nothing else. It exists to try GitHub's
hosted macOS runner as an alternative to Azure Pipelines' still-preview `macOS-26` image for
building the Oktavis iOS app (PBI 230). The Oktavis source itself is never committed here — the
workflow clones it fresh from Azure DevOps at build time via a read-only PAT stored as a repo
secret.

Run it from the **Actions** tab → "Oktavis iOS TestFlight (GitHub-hosted macOS runner)" → **Run
workflow**, choosing the Azure DevOps branch to build.

Required repo secrets (Settings → Secrets and variables → Actions):

| Secret | Purpose |
|---|---|
| `AZDO_PAT` | Read-only Azure DevOps PAT (Code: Read) to clone the source |
| `IOS_DIST_P12_BASE64` | base64 of the Apple distribution cert (`ios_dist.p12`) |
| `P12_PASSWORD` | Export password for the .p12 |
| `PROVISION_PROFILE_BASE64` | base64 of `oktavis_appstore.mobileprovision` |
| `ASC_AUTH_KEY_BASE64` | base64 of the App Store Connect API key (`AuthKey_ASC.p8`) |
| `ASC_KEY_ID` | App Store Connect API key id |
| `ASC_ISSUER_ID` | App Store Connect API issuer id |
| `OKTAVIS_NUGET_USER` | Username for the internal `oktavis` NuGet feed |
| `OKTAVIS_NUGET_PASS` | Password for the internal `oktavis` NuGet feed |
