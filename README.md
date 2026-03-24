# solivram

<p align="center">
  <img src="solivram.png" alt="solivram logo" width="160"/>
</p>

![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)
![Version](https://img.shields.io/badge/version-0.2.0-blue)
![Rust](https://img.shields.io/badge/built%20with-Rust-orange)
![Origine](https://img.shields.io/badge/origine-France-blue)
![Stars](https://img.shields.io/github/stars/Solivram/solivram?style=social)

🇫🇷 [Français](README.md) · 🇬🇧 [English](README_EN.md)

> Infrastructure distribuée haute disponibilité, sécurisée post-quantique, observable et extensible, conçue en Rust pur pour des environnements critiques.

<p align="center">
  <a href="https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/solivram_0.2.0_amd64.deb">
    <img src="https://img.shields.io/badge/⬇️%20Télécharger%20solivram%20v0.2.0%20(.deb)-2ea44f?style=for-the-badge" alt="Télécharger"/>
  </a>
</p>

**Auteur** : Jenka Nauta — France
**Version** : 0.2.0 — 2026-03-24 — Phase 224 — 1479 tests
**Type** : Post-Quantum Infrastructure Engine
**Releases** : [solivram-releases](https://github.com/Solivram/solivram-releases/releases)

---

## Catégories

`Sécurité` · `Infrastructure distribuée` · `Post-Quantum Cryptography` · `Rust`

<p align="center">
  <img src="https://raw.githubusercontent.com/Solivram/solivram/main/images/shema_technique_solivram.png" alt="Schéma technique des services solivram v0.2.0" width="100%"/>
</p>

---

## Capacités principales

| Module | Description |
|--------|-------------|
| **Cluster Raft HA** | Élection, réplication, snapshot, membership dynamique |
| **PKI X.509 interne** | CA racine, intermédiaire, feuilles, CRL |
| **DNS souverain + DNSSEC** | Dual P-256 + ML-DSA-65 |
| **Hybridation PQC** | ML-KEM-768 (encapsulation) + ML-DSA-65 (signature) |
| **API REST** | Axum — auth Bearer, RBAC 5 rôles, rate-limiter, CORS |
| **Stockage chiffré** | redb + AES-256-GCM + rotation des clés |
| **Reverse proxy HA** | Circuit-breaker, backends dynamiques |
| **Chiffrement E2E** | ML-KEM-768 + AES-256-GCM, bout en bout entre clients |
| **Trust inter-nœuds** | Signaux de confiance, API admin accept/revoke |
| **GUI native** | Interface egui |
| **Sessions sécurisées** | TTL 1h + 2FA TOTP RFC 6238 |

---

## Cibles

- Équipes DevOps / SRE cherchant une infra Rust production-grade
- Entreprises PKI nécessitant une CA interne auditable
- Chercheurs en cryptographie post-quantique (PQC)
- Éditeurs SaaS B2B requérant haute disponibilité et conformité

---

## Prérequis système

- **OS** : Debian 11+ / Ubuntu 20.04+ (amd64 x86-64)
- **Architecture** : x86-64 uniquement

```bash
uname -m  # doit afficher x86_64
```

## Installation

```bash
curl -LO https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/solivram_0.2.0_amd64.deb && sudo dpkg -i solivram_0.2.0_amd64.deb
solivram --help
```

**Dépendances** : `libwayland-client0` · `libudev1` · `libasound2` · `libgcc-s1` · `libc6` · `libffi8` · `libcap2`

```bash
sudo setcap cap_net_bind_service=+ep /usr/bin/solivram
```

---

## Vérification de signature

```bash
solivram identity:verify
# ✅ P-256 valide | ✅ ML-DSA valide
```

**Clé publique P-256 :**
```
04fa81886487fa97a92bf77756252ffbb17cfdec1ca55131e7bf94920a14f00faf6af84fb9680f1d3c367cba6c09fa17dc1e2edd3005173ed599fcc091973a3091
```

---

## Premier démarrage

```bash
solivram --config /etc/solivram/default.toml headless
solivram --config /etc/solivram/default.toml api
```

## Désinstallation

```bash
sudo dpkg -r solivram
```

---

## Documentation

| Document | Français | English |
|----------|----------|---------|
| **Mise en garde & cartographie** | [Solivram_Mise_En_Garde_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Mise_En_Garde_FR.pdf) | [Solivram_Warning_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Warning_EN.pdf) |
| **Quickstart** | [Solivram_Quickstart_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Quickstart_FR.pdf) | [Solivram_Quickstart_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Quickstart_EN.pdf) |
| **Vue d'ensemble** | [Solivram_Overview_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Overview_FR.pdf) | [Solivram_Overview_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Overview_EN.pdf) |
| **Guide administrateur** | [Solivram_Guide_Admin_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Guide_Admin_FR.pdf) | [Solivram_Guide_Admin_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Guide_Admin_EN.pdf) |
| **Configuration production** | [Solivram_Config_Prod_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Config_Prod_FR.pdf) | [Solivram_Config_Prod_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Config_Prod_EN.pdf) |
| **Configuration complète** | [Solivram_Config_Prod_full_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Config_Prod_full_FR.pdf) | [Solivram_Config_Prod_full_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Config_Prod_full_EN.pdf) |
| **Exception hot-reload security_level** | [FR](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Exception_Hot_Reload_Security_Level_FR.pdf) | [EN](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Exception_Hot_Reload_Security_Level_EN.pdf) |
| **Roadmap v0.2.0** | [Solivram_Roadmap_v0.2.0_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Roadmap_v0.2.0_FR.pdf) | [Solivram_Roadmap_v0.2.0_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Roadmap_v0.2.0_EN.pdf) |
| **Architecture** | [Solivram_Architecture.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Architecture.pdf) | [Solivram_Architecture_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Architecture_EN.pdf) |
| **Manuel développeur** | [Solivram_Manuel_Dev.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Manuel_Dev.pdf) | [Solivram_Manuel_Dev_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Manuel_Dev_EN.pdf) |

---

## FAQ

**Q : Rust doit-il être installé pour utiliser solivram ?**
Non. Le paquet `.deb` contient un binaire déjà compilé. Rust n'est requis que pour compiler depuis les sources.

**Q : Solivram fonctionne-t-il sur ARM / Raspberry Pi ?**
Pas encore. Seule l'architecture amd64 (x86-64) est supportée en v0.2.0.

**Q : Le binaire est-il signé ?**
Oui. Solivram embarque une identité P-256 + ML-DSA-65 vérifiable via `solivram identity:verify`.

**Q : Comment mettre à jour solivram ?**
```bash
curl -LO https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/solivram_0.2.0_amd64.deb && sudo dpkg -i solivram_0.2.0_amd64.deb
```

## Pitchs sectoriels

| Secteur | Français | English |
|---------|----------|---------|
| Défense | [Pitch_Defense_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Pitch_Defense_FR.pdf) | [Pitch_Defense_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Pitch_Defense_EN.pdf) |
| Santé | [Pitch_Sante_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Pitch_Sante_FR.pdf) | [Pitch_Healthcare_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Pitch_Healthcare_EN.pdf) |
| Finance | [Pitch_Finance_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Pitch_Finance_FR.pdf) | [Pitch_Finance_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Pitch_Finance_EN.pdf) |
| Agents IA | [Pitch_Agents_IA_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Pitch_Agents_IA_FR.pdf) | [Pitch_Agents_IA_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Pitch_Agents_IA_EN.pdf) |
| Énergie / Industrie | [Pitch_Energie_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Pitch_Energie_FR.pdf) | [Pitch_Energy_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Pitch_Energy_EN.pdf) |
| Administrations | [Pitch_Admin_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Pitch_Admin_FR.pdf) | [Pitch_Admin_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.2.0/Solivram_Pitch_Admin_EN.pdf) |

---

*solivram — Jenka Nauta — France — 2026*
