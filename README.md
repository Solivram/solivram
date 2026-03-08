# solivram

![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)
![Version](https://img.shields.io/badge/version-0.1.0-blue)
![Rust](https://img.shields.io/badge/built%20with-Rust-orange)
![Origine](https://img.shields.io/badge/origine-France-blue)

> Infrastructure distribuée haute disponibilité, sécurisée post-quantique,
> observable et extensible, conçue en Rust pur pour des environnements critiques.

**Auteur** : Jenka Nauta — France
**Version** : 0.1.0 — 2026-03-08
**Type** : Serveur / Daemon
**Releases** : [solivram-releases](https://github.com/Solivram/solivram-releases/releases)

---

## Catégories

`Sécurité` · `Infrastructure distribuée` · `Post-Quantum Cryptography` · `Rust`

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
| **GUI native** | Interface egui |
| **Sessions sécurisées** | TTL 1h + 2FA TOTP RFC 6238 |

---

## Cibles

- Équipes DevOps / SRE cherchant une infra Rust production-grade
- Entreprises PKI nécessitant une CA interne auditable
- Chercheurs en cryptographie post-quantique (PQC)
- Éditeurs SaaS B2B requérant haute disponibilité et conformité

---

## Exemple — Autorité de certification

Une autorité de certification déploie solivram pour :

- Gérer sa PKI X.509 (CA racine, intermédiaire, feuilles, CRL)
- Stocker les clés en AES-256-GCM avec rotation automatique
- Signer en post-quantique via ML-DSA-65
- Contrôler les accès par rôles (Admin / Opérateur / Superviseur / Lecteur / Invité) avec 2FA TOTP RFC 6238
- Assurer la haute disponibilité via cluster Raft multi-nœuds
- Auditer chaque opération via API REST Bearer + RBAC

---

## Installation

### Debian / Ubuntu

```bash
# Télécharger depuis la page releases
sudo dpkg -i solivram_0.1.0_amd64.deb
solivram --help
```

**Dépendances** : `libwayland-client0` · `libudev1` · `libasound2` · `libgcc-s1` · `libc6` · `libffi8` · `libcap2`

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

## Pitchs sectoriels

| Secteur | Français | English |
|---------|----------|---------|
| Défense | [Pitch_Defense_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.1.0/Solivram_Pitch_Defense_FR.pdf) | [Pitch_Defense_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.1.0/Solivram_Pitch_Defense_EN.pdf) |
| Santé | [Pitch_Sante_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.1.0/Solivram_Pitch_Sante_FR.pdf) | [Pitch_Healthcare_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.1.0/Solivram_Pitch_Healthcare_EN.pdf) |
| Finance | [Pitch_Finance_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.1.0/Solivram_Pitch_Finance_FR.pdf) | [Pitch_Finance_EN.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.1.0/Solivram_Pitch_Finance_EN.pdf) |
| Agents IA | [Pitch_Agents_IA_FR.pdf](https://github.com/Solivram/solivram-releases/releases/download/v0.1.0/Solivram_Pitch_Agents_IA_FR.pdf) | — |

---

## Téléchargement

➡️ [**solivram v0.1.0 — Releases**](https://github.com/Solivram/solivram-releases/releases/tag/v0.1.0)

---

*solivram — Jenka Nauta — France — 2026*
