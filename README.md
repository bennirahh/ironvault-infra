# ⚙️ IRONVAULT: Infrastructure as Code

![NixOS](https://img.shields.io/badge/OS-NixOS-blueviolet?logo=nixos&logoColor=white)
![Flakes](https://img.shields.io/badge/Nix-Flakes-blue?logo=nixos)
![Status](https://img.shields.io/badge/status-initialization-orange)
![Author](https://img.shields.io/badge/author-Bennirahh-white?logo=github)

> **The engine room of the IRONVAULT sovereign cluster.**  
> *Declarative, reproducible, and immutable bare-metal management.*

---

## 🏗️ Technical Stack

<details open>
<summary><b>Core Infrastructure</b></summary>

* **Operating System:** ![NixOS](https://img.shields.io/badge/NixOS-24.11-blueviolet?style=flat-square&logo=nixos) (Immutable & Declarative)
* **Provisioning:** ![Nix Flakes](https://img.shields.io/badge/Nix_Flakes-Hermetic-blue?style=flat-square&logo=nixos) (Deterministic deployments)
* **Networking:** ![WireGuard](https://img.shields.io/badge/WireGuard-Zero--Trust-orange?style=flat-square&logo=wireguard) (Encrypted Mesh Network)
</details>

<details>
<summary><b>Security & Storage</b></summary>

* **Secret Management:** ![sops-nix](https://img.shields.io/badge/sops--nix-Age-green?style=flat-square) (GitOps-friendly encryption)
* **Storage:** ![ZFS](https://img.shields.io/badge/Storage-ZFS-blue?style=flat-square) (Data Integrity & Snapshots)
* **Future Expansion:** High-availability storage (Ceph/Longhorn) planned for Phase 4.
</details>


## 📂 Repository Structure

```text
.
├── flake.nix             # Infrastructure entry point
├── flake.lock            # Exact version pinning
├── hosts/                # Node-specific configurations
│   └── node-01/          # Primary Control Plane
│       └── configuration.nix
├── modules/              # Reusable system profiles
│   ├── core/             # Base system hardening
│   ├── network/          # Firewall & Mesh VPN
│   └── services/         # K3s, Databases, etc.
└── scripts/              # Maintenance & deployment tools
```

---

## 🚀 Getting Started

### Prerequisites

- Nix installed with `flakes` and `nix-command` enabled.
- SSH access to the target bare-metal node.

### 🔎 Local Evaluation

To check if the configuration for **node-01** builds correctly without deploying:

```bash
nix build .#nixosConfigurations.node-01.config.system.build.toplevel
```

### 🚀 Remote Deployment

To deploy and activate the configuration on a live node:

```bash
nixos-rebuild switch --flake .#node-01 --target-host root@<node-ip>
```

---

## 🔗 Project Ecosystem

- **Strategy & Governance:**  
  https://github.com/Bennirahh/ironvault-docs

- **Security Compliance (ADR-001):**  
 https://github.com/bennirahh/ironvault-docs/blob/main/docs/001-physical-infrastructure-selection.md

---
![License](https://img.shields.io/badge/license-MIT-blue)
![Author](https://img.shields.io/badge/author-Bennirahh-white?style=flat&logo=github)

