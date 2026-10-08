# oocbor: Sovereign CBOR SERIALIZER

<div align="center">

```
================================================================================
                                oocbor
               Sovereign openOODA CBOR SERIALIZER
================================================================================
```

**Sovereign CBOR SERIALIZER**  
*Concise Binary Object Representation encoder, diagnostic viewer, and decoder (RFC 8949).*  
*Two Faces, One Engine:* Modern terminal ergonomics for humans • Zero-leakage MCP for AI agents  
Written in 100% pure [openOODA](https://github.com/openOODA).

[![License: Apache-2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![openOODA](https://img.shields.io/badge/openOODA-1.0-emerald.svg)](https://openooda.org)
[![Architecture: x86_64 | aarch64](https://img.shields.io/badge/Arch-x86__64%20%7C%20aarch64-lightgrey.svg)]()

</div>

---

## 1. Quick Install

### Automated Installer (Linux x86_64 & aarch64)
```bash
curl -fsSL https://openooda-tools.github.io/oocbor/install.sh | bash
```

### Native Package Managers
```bash
# Arch Linux (AUR / PKGBUILD)
yay -S oocbor-bin
# Or manual PKGBUILD:
cd packaging/arch && makepkg -si

# Debian / Ubuntu (.deb)
curl -fsSL https://openooda-tools.github.io/oocbor/install.sh | bash -s -- --deb

# Fedora / RHEL (.rpm)
curl -fsSL https://openooda-tools.github.io/oocbor/install.sh | bash -s -- --rpm
```

### Uninstallation
```bash
oocbor-uninstall
# or: curl -fsSL https://openooda-tools.github.io/oocbor/uninstall.sh | bash
```

---

## 2. CLI Usage

```
usage: oocbor [options] [HEX_OR_JSON]

Concise Binary Object Representation encoder, diagnostic viewer, and decoder.

Options:
  -d, --decode         decode CBOR hex stream to diagnostic/json [default]
  -e, --encode         encode JSON object into CBOR binary hex
  -i, --inspect        inspect CBOR major types, byte offsets, and layout
  -t, --to <FORMAT>    target format: json, cbor, diag
      --diag           output RFC 8949 diagnostic notation
      --json           output formatted as structured JSON
      --demo           use built-in sample CBOR stream
      --mcp            run as Model Context Protocol stdio server
  -h, --help           display this help and exit
  -v, --version        output version information and exit
```

### Examples
```bash
# Decode CBOR hex payload with full diagnostic panel
oocbor a266656e67696e65666f6f63626f726776657273696f6e02

# Inspect byte layout and major type headers
oocbor -i a266656e67696e65666f6f63626f726776657273696f6e02

# Decode to clean JSON
oocbor --to json a266656e67696e65666f6f63626f726776657273696f6e02

# Output RFC 8949 diagnostic notation
oocbor --diag a266656e67696e65666f6f63626f726776657273696f6e02
```

---

## 3. Model Context Protocol (MCP)

When invoked with `--mcp`, `oocbor` runs a JSON-RPC 2.0 stdio server providing structured tools for AI coding agents:

```bash
oocbor --mcp
```

### Exported Tools
* `cbor_decode`: Decode CBOR hex payload into JSON and diagnostic notation.
* `cbor_encode`: Encode key-value pairs into CBOR binary hex.
* `cbor_inspect`: Inspect CBOR item layout, major types, and byte offsets.
* `cbor_diag`: Format CBOR hex payload into RFC 8949 diagnostic notation.
* `cbor_stats`: Compute CBOR payload statistics and item counts.

---

## 4. Theming Integration (`oote`)

`oocbor` synchronizes visual styles and status colors with [oote](https://github.com/openOODA-tools/oote):
* **Configuration:** Reads active palette from `~/.openooda/theme.oot`.
* **Environment Overrides:** Respects `$OODA_THEME` and `$NO_COLOR`.

---

## 5. Security & Zero Ambient Authority

* **Pure Capability Bounded:** Operates strictly with explicit tokens (`&FsReadCap`, `&ProcessCap`, `&EnvCap`). Physical absence of ambient disk/net leakage.
* **Negative-Trust Architecture:** Strict input validation and operational limits.
* **Hermetic Binary:** Standalone zero-dependency executable.

---

## 6. License

Apache License, Version 2.0. See [LICENSE](LICENSE) for details.
