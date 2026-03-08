# solivram

<p align="center">
  <img src="solivram.png" alt="solivram logo" width="160"/>
</p>

![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)
![Version](https://img.shields.io/badge/version-0.1.0-blue)
![Rust](https://img.shields.io/badge/built%20with-Rust-orange)
![Origin](https://img.shields.io/badge/origin-France-blue)
[![🇫🇷 Français](https://img.shields.io/badge/🇫🇷%20Français-0055A4)](https://github.com/Solivram/solivram/blob/main/README.md)
[![🇬🇧 English](https://img.shields.io/badge/🇬🇧%20English-012169)](https://github.com/Solivram/solivram/blob/main/README_EN.md)

> High-availability distributed infrastructure, post-quantum secured, observable and extensible, built in pure Rust for critical environments.

<p align="center">
  <a href="https://github.com/Solivram/solivram-releases/releases">
    <img src="https://img.shields.io/badge/⬇️%20Download%20solivram%20v0.1.0-2ea44f?style=for-the-badge" alt="Download"/>
  </a>
</p>

**Author** : Jenka Nauta — France
**Version** : 0.1.0 — 2026-03-08
**Type** : Server / Daemon
**Releases** : [solivram-releases](https://github.com/Solivram/solivram-releases/releases)

---

## Categories

`Security` · `Distributed Infrastructure` · `Post-Quantum Cryptography` · `Rust`

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
| **Native GUI** | egui interface |
| **Secure Sessions** | TTL 1h + 2FA TOTP RFC 6238 |

---

## Target users

- DevOps / SRE teams looking for production-grade Rust infrastructure
- PKI enterprises requiring an auditable internal CA
- Post-quantum cryptography researchers
- B2B SaaS vendors requiring high availability and compliance

---

## Example — Certificate Authority

A certificate authority deploys solivram to:

- Manage its X.509 PKI (root CA, intermediate, leaf certs, CRL)
- Store keys in AES-256-GCM with automatic rotation
- Sign post-quantum via ML-DSA-65
- Control access by roles (Admin / Operator / Supervisor / Reader / Guest) with 2FA TOTP RFC 6238
- Ensure high availability via multi-node Raft cluster
- Audit every operation via Bearer REST API + RBAC

---

## Installation

### Debian / Ubuntu

```bash
# Download from the releases page
sudo dpkg -i solivram_0.1.0_amd64.deb
solivram --help
```

**Dependencies** : `libwayland-client0` · `libudev1` · `libasound2` · `libgcc-s1` · `libc6` · `libffi8` · `libcap2`

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

## Documentation

| Document | Français | English |
|----------|----------|---------|
| **Quickstart** | [Solivram_Quickstart.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.1.0/Solivram_Quickstart.pdf) | [Solivram_Quickstart_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.1.0/Solivram_Quickstart_EN.pdf) |

---

## Sector pitches

| Sector | Français | English |
|--------|----------|---------|
| Defense | [Pitch_Defense_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.1.0/Solivram_Pitch_Defense_FR.pdf) | [Pitch_Defense_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.1.0/Solivram_Pitch_Defense_EN.pdf) |
| Healthcare | [Pitch_Sante_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.1.0/Solivram_Pitch_Sante_FR.pdf) | [Pitch_Healthcare_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.1.0/Solivram_Pitch_Healthcare_EN.pdf) |
| Finance | [Pitch_Finance_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.1.0/Solivram_Pitch_Finance_FR.pdf) | [Pitch_Finance_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.1.0/Solivram_Pitch_Finance_EN.pdf) |
| AI Agents | [Pitch_Agents_IA_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.1.0/Solivram_Pitch_Agents_IA_FR.pdf) | [Pitch_Agents_IA_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.1.0/Solivram_Pitch_Agents_IA_EN.pdf) |

---

*solivram — Jenka Nauta — France — 2026*
