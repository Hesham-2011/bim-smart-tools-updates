# BIM Smart Tools - update manifests

Tiny public JSON files that the installed Revit and Navisworks suites poll to
learn whether a newer version exists. Each suite only reads its own file and
never writes to this repo.

- `revit-manifest.json` - checked by the **01) Revit** suite
- `navisworks-manifest.json` - checked by the **02) Navisworks** suite

## Fields

- `latestVersion` - plain version string, e.g. `1.0.2`. Must exactly match the
  version the suite's installer was built with (Revit: `version.txt`;
  Navisworks: the `<Version>` in `ClashTestManager.csproj` and
  `Installer.csproj`, which must be kept equal).
- `downloadUrl` - the suite's public Google Drive folder link ("Anyone with
  the link - Viewer"). Shown to the user via an "Open Download Folder" button;
  nothing is downloaded automatically.

## Publishing a new release - see each suite's README for the full checklist.

The short version: build and upload the new installer **first**, then edit
this file's `latestVersion` (and `downloadUrl` if it changed) **last** - only
after the file is actually live on Drive - since bumping `latestVersion`
immediately starts notifying existing users.

Edit directly on GitHub: open the file, click the pencil (edit) icon, change
the value, commit to `main`. No local git needed.
