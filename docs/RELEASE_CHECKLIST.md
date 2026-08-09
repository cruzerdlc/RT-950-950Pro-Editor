# v0.8.40 Release Checklist

- [ ] Confirm `VERSION`, `CHANGELOG.md`, and README show `v0.8.40`.
- [ ] Build a clean Windows package and test application launch.
- [ ] Test USB/COM read and write when hardware is available.
- [ ] Test BLE read and write when hardware is available.
- [ ] Confirm the updater identifies the correct version.
- [ ] Generate a SHA-256 checksum for every release asset.
- [ ] Create and push the `v0.8.40` tag.
- [ ] Create the GitHub Release titled `RT-950/950Pro Editor v0.8.40`.
- [ ] Upload the verified release ZIP and checksum file.
- [ ] Verify the downloaded asset and its checksum.
- [ ] Confirm antivirus documentation is linked from the release.
- [ ] Announce the release.

`SHA256SUMS.txt` currently records files from the packaged application and is not a
concise public release-asset checksum list. Publish a separate release checksum in
the form `<SHA256>  RT950_v0.8.40.zip` only after hashing the verified archive.
