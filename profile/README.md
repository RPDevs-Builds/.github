# ⚙️ RPDevs-Builds Compilation & Release Fleet

Welcome to the distribution and build hub of **RPDevs**. This organization operates as a high-performance, self-hosted continuous integration fleet dedicated to automated cross-compilation, packaging, and software release pipelines across RF, embedded, desktop, and mobile architectures.

---

## 🏗️ The 2-Core Architecture

RPDevs-Builds operates on a consolidated 2-Core management paradigm to minimize overhead and enforce organizational consistency:

| Core Engine | Purpose | Key Responsibilities |
| :--- | :--- | :--- |
| **[devops-manager](https://github.com/RPDevs-Builds/devops-manager)** | 🛡️ **Operational Hub** | Fleet Orchestration, Archival Lifecycle, Global Health Checks, Security Governance, and Notifications. |
| **[builder-manager](https://github.com/RPDevs-Builds/builder-manager)** | 🏭 **Registry Engine** | Cross-compilation matrices, release packaging logic, and centralized build dependency management. |

---

## 🚀 The Self-Hosted Runner Fleet & NFS Cache

Our pipelines run exclusively on our sovereign bare-metal hardware (`linux64` runners like T430 and llmadmin01) bypassing standard GitHub hosted limits.

```
+-------------------------------------------------------------------------------+
|                             RPDevs-Builds Pipeline                            |
+-------------------------------------------------------------------------------+
|                                                                               |
|   [GitHub Repos] ----> [Self-Hosted Runner] <---> [Cloudflare ZT Tunnel]      |
|                              |                              |                 |
|                              v                              v                 |
|                       [Cross-Compiler]              [NFS Cache Storage]       |
|                     (GCC/Clang/MSVC/SDK)         (/mnt/sharedroot/shared)     |
|                              |                                                |
|                              v                                                |
|         [GitHub Releases / Packages] <---- [fetch_latest.py]                  |
|                              |                                                |
|                              v                                                |
|                 [rpdevs-builds.github.io Index]                               |
|                                                                               |
+-------------------------------------------------------------------------------+
```

### ⚡ Centralized Caching
Instead of pulling toolchains and dependencies repeatedly over the WAN, all our self-hosted runners inject global cache targets for `ccache`, `pip`, `npm`, `cargo`, and `go` directly to a high-speed NFS mount point (`/mnt/sharedroot/github_runners/shared`). The NFS storage is mounted securely over **Cloudflare TCP Tunnels**, bypassing firewall limitations while keeping transit fully encrypted.

---

## 🛠️ Project Ecosystem

While `devops-manager` and `builder-manager` handle the orchestration, the actual compilation matrix spans numerous projects:

*   **Core Systems:** `kexecboot.xyz`, `xbmc-build`, `vlc-live-555`
*   **OpenWrt & Embedded:** `blackhole-server`, `openwrt-blackhole-feed`, `luci-app-nfs`
*   **Browser & Media Addons:** `nextdns-firefox-addon`, `kodi-addons`, `script.service.*`, `inputstream.*`
*   **Release Gateway:** `rpdevs-builds.github.io` (a decoupled static frontend that polls the GitHub API for our releases).

### 📦 [View Released Packages](https://github.com/orgs/RPDevs-Builds/packages)

*This organization operates as a public utility powered by sovereign automation workflows. Privacy by Default: Zero analytics, telemetry, or tracking embedded into any compiled releases.*
