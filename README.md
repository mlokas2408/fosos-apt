# fosos-apt

The public FosOS package archive. Installed systems use the `stable` suite.
New packages are published to `testing` first and copied to `stable` only
after that exact package has been tested.

```text
https://mlokas2408.github.io/fosos-apt
```

GitHub Pages needs to serve this repository from the `main` branch root.
The archive signing private key is not in this repository. The public key is
`fosos-archive-keyring.gpg`, and its fingerprint is in `FINGERPRINT`.

An installed FosOS system already has this source through the
`fosos-archive-keyring` package. To add it by hand:

```bash
sudo install -m 0644 fosos-archive-keyring.gpg /usr/share/keyrings/fosos-archive-keyring.gpg
sudo tee /etc/apt/sources.list.d/fosos.sources >/dev/null <<'EOF'
Types: deb
URIs: https://mlokas2408.github.io/fosos-apt
Suites: stable
Components: main
Signed-By: /usr/share/keyrings/fosos-archive-keyring.gpg
EOF
sudo apt update
```

`dists/` and `pool/` are produced by `reprepro` in the FosOS source
repository. Do not edit those files by hand.
