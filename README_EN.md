# solivram

<p align="center">
  <img src="solivram.png" alt="solivram logo" width="160"/>
</p>

![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)
![Version](https://img.shields.io/badge/version-0.2.0-blue)
![Rust](https://img.shields.io/badge/built%20with-Rust-orange)
![Origin](https://img.shields.io/badge/origin-France-blue)
![Stars](https://img.shields.io/github/stars/Solivram/solivram?style=social)

<p align="center">
  <a href="https://github.com/Solivram/solivram/blob/main/README.md"><strong>🇫🇷 Français</strong></a>
  &nbsp;·&nbsp;
  <a href="https://github.com/Solivram/solivram/blob/main/README_EN.md"><strong>🇬🇧 English</strong></a>
</p>

> High-availability distributed infrastructure, post-quantum secured, observable and extensible, built in pure Rust for critical environments.

<p align="center">
  <a href="https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/solivram_0.2.0_amd64.deb">
    <img src="https://img.shields.io/badge/⬇️%20Download%20solivram%20v0.2.0%20(.deb)-2ea44f?style=for-the-badge" alt="Download"/>
  </a>
</p>

**Author** : Jenka Nauta — France
**Version** : 0.2.0 — 2026-04-06 — Phase 271 — 1722 tests
**Type** : Post-Quantum Infrastructure Engine
**Releases** : [solivram-releases](https://github.com/Solivram/solivram-releases/releases)

---

## Categories

`Security` · `Distributed Infrastructure` · `Post-Quantum Cryptography` · `Rust`

<p align="center">
  <img src="https://raw.githubusercontent.com/Solivram/solivram/main/images/shema_technique_solivram.png" alt="solivram v0.2.0 — Technical services diagram" width="100%"/>
</p>

---

## Core capabilities

| Module | Description |
|--------|-------------|
| **Raft HA Cluster** | Election, replication, snapshot, dynamic membership |
| **Internal X.509 PKI** | Root CA, intermediate, leaf certs, CRL |
| **Sovereign DNS + DNSSEC** | Dual P-256 + ML-DSA-65 |
| **PQC Hybridization** | ML-KEM-768 (encapsulation) + ML-DSA-65 (signature) |
| **REST API** | Axum — Bearer auth, RBAC 5 roles, rate-limiter, CORS |
| **Encrypted Storage** | redb + AES-256-GCM + key rotation |
| **HA Reverse Proxy** | Circuit-breaker, dynamic backends |
| **E2E Encryption** | ML-KEM-768 + AES-256-GCM, end-to-end between clients |
| **Inter-node Trust** | Trust signals, admin accept/revoke API |
| **Native GUI** | egui interface |
| **Secure Sessions** | TTL 1h + 2FA TOTP RFC 6238 |
| **nftables Firewall** | Integrated nftables management — strict/permissive modes, ambient capabilities, declarative outbound whitelist |
| **Inter-cluster Federation** | KV/CRL sync across clusters, quarantine, federated trust |
| **Encrypted Backup** | AES-256-GCM snapshots, remote upload, automatic scheduler |
| **Cognitive Memory** | 18 `/api/memory/*` endpoints, SQLite WAL, TF-IDF, TOML rate limiters |

---

## Target audiences

- DevOps / SRE teams looking for a production-grade Rust infrastructure
- PKI enterprises requiring an auditable internal CA
- Post-quantum cryptography (PQC) researchers
- B2B SaaS vendors requiring high availability and compliance

---

## System requirements

- **OS** : Debian 11+ / Ubuntu 20.04+ (amd64 x86-64)
- **Architecture** : x86-64 only

```bash
uname -m  # should display x86_64
```

## Installation

```bash
curl -LO https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/solivram_0.2.0_amd64.deb && sudo apt install ./solivram_0.2.0_amd64.deb
solivram --help
```

| | Value | Detail |
|--|-------|--------|
| **Download** | ~19 MB | Compressed `.deb` archive |
| **Installed on disk** | ~79 MB | Uncompressed Rust binary |

**Dependencies** : `libwayland-client0` · `libudev1` · `libasound2` · `libgcc-s1` · `libc6` · `libffi8` · `libcap2` · `libcap2-bin` · `nftables`

```bash
sudo setcap cap_net_bind_service=+ep /usr/bin/solivram
```

---

## Signature verification

```bash
solivram identity:verify
# ✅ P-256 valid | ✅ ML-DSA valid
```

**P-256 public key:**
```
04fa81886487fa97a92bf77756252ffbb17cfdec1ca55131e7bf94920a14f00faf6af84fb9680f1d3c367cba6c09fa17dc1e2edd3005173ed599fcc091973a3091
```

---

## First start

```bash
solivram --config /etc/solivram/default.toml headless
solivram --config /etc/solivram/default.toml api
```

## Uninstall

```bash
# Uninstall (keeps config and data)
sudo apt remove solivram

# Full uninstall (also removes config files)
sudo apt purge solivram

# Full data removal (databases, certificates, keys)
sudo rm -rf /var/lib/solivram/ /etc/solivram/
```

---

#### Hot reload
- Edit `[firewall.outbound_services]` in `config.toml`
- `POST /api/config/reload` → NftablesManager rebuilds `chain output` + `chain input` without restart
- `sections_modifiees()` automatically detects `[firewall]` changes

---

### Example:

Reload configuration from default.toml via your terminal.

- Authenticate:

> export ADMIN_TOKEN=$(sudo grep '^admin_token' /etc/solivram/default.toml | cut -d'"' -f2)

- Reload: example for `api_hostname` variable configured in default.toml

> curl -s -X POST "https://solivram.rust:8080/api/config/reload" -H "Authorization: Bearer $ADMIN_TOKEN" | python3 -m json.tool

---

## Documentation

| Document | Français | English |
|----------|----------|---------|
| **Warning & map** | [Solivram_Mise_En_Garde_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Mise_En_Garde_FR.pdf) | [Solivram_Warning_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Warning_EN.pdf) |
| **Quickstart** | [Solivram_Quickstart_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Quickstart_FR.pdf) | [Solivram_Quickstart_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Quickstart_EN.pdf) |

---

## FAQ

**Q: Does Rust need to be installed to use solivram?**
No. The `.deb` package contains a pre-compiled binary. Rust is only required to build from source.

**Q: Does solivram work on ARM / Raspberry Pi?**
Not yet. Only amd64 (x86-64) architecture is supported in v0.2.0.

**Q: Is the binary signed?**
Yes. Solivram embeds a P-256 + ML-DSA-65 identity verifiable via `solivram identity:verify`.

**Q: How to update solivram?**
```bash
curl -LO https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/solivram_0.2.0_amd64.deb && sudo apt install ./solivram_0.2.0_amd64.deb
```

## Sector pitches

| Sector | Français | English |
|--------|----------|---------|
| Defense | [Pitch_Defense_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Pitch_Defense_FR.pdf) | [Pitch_Defense_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Pitch_Defense_EN.pdf) |
| Healthcare | [Pitch_Sante_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Pitch_Sante_FR.pdf) | [Pitch_Healthcare_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Pitch_Healthcare_EN.pdf) |
| Finance | [Pitch_Finance_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Pitch_Finance_FR.pdf) | [Pitch_Finance_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Pitch_Finance_EN.pdf) |
| AI Agents | [Pitch_Agents_IA_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Pitch_Agents_IA_FR.pdf) | [Pitch_Agents_IA_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Pitch_Agents_IA_EN.pdf) |
| Energy / Industry | [Pitch_Energie_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Pitch_Energie_FR.pdf) | [Pitch_Energy_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Pitch_Energy_EN.pdf) |
| Government | [Pitch_Admin_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Pitch_Admin_FR.pdf) | [Pitch_Admin_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Pitch_Admin_EN.pdf) |

---

*solivram — Jenka Nauta — France — 2026*
