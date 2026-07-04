# ⚙️ RPDevs-Builds Compilation & Release Fleet

Welcome to the distribution and build hub of **RPDevs**. This organization is a high-performance continuous integration fleet dedicated to automated cross-compilation, package feed packaging, and software release pipelines across RF, embedded, desktop, and mobile architectures.

---

## 🛠️ The Compilation & Release Ecosystem

| Repository | Purpose | Target / Environment | Release Status |
| :--- | :--- | :--- | :--- |
| **[github-actions-repo](https://github.com/RPDevs-Builds/github-actions-repo)** | 📋 **Template Registry**: Standardized, production-ready workflows. | GitHub Actions CI/CD | ![CI Validate](https://github.com/RPDevs-Builds/github-actions-repo/actions/workflows/validate.yml/badge.svg) |
| **[kodi-build](https://github.com/RPDevs-Builds/kodi-build)** | 🎬 **Kodi Core Builder**: Auto-compiling Kodi Omega (v21) & Master (v22). | Win64, Linux, macOS, Android | ![Build Status](https://github.com/RPDevs-Builds/kodi-build/actions/workflows/build-release.yml/badge.svg) |
| **[rpdevs-builds.github.io](https://github.com/RPDevs-Builds/rpdevs-builds.github.io)** | 🌐 **Release Gateway**: Redirect index site showing compiled release builds. | Pages / GitHub API | ![Pages Status](https://github.com/RPDevs-Builds/rpdevs-builds.github.io/actions/workflows/pages.yml/badge.svg) |
| **[blackhole-server](https://github.com/RPDevs-Builds/blackhole-server)** | 🛡️ **Privacy Sink**: Golang webserver to intercept telemetric traffic. | OpenWRT (ARM64/AMD64) | ![Go Build](https://github.com/RPDevs-Builds/blackhole-server/actions/workflows/go.yml/badge.svg) |
| **[luci-app-blackhole](https://github.com/RPDevs-Builds/luci-app-blackhole)** | 🖥️ **LuCI App**: OpenWRT Web GUI module to manage the Blackhole server. | LuCI Client Model | ![LuCI Validate](https://github.com/RPDevs-Builds/luci-app-blackhole/actions/workflows/luci.yml/badge.svg) |
| **[openwrt-blackhole-feed](https://github.com/RPDevs-Builds/openwrt-blackhole-feed)** | 📦 **Custom Package Feed**: Automated feed hosting compiled `.apk`/`.ipk`. | OpenWRT Package SDK | ![SDK Compile](https://github.com/RPDevs-Builds/openwrt-blackhole-feed/actions/workflows/sdk-build.yml/badge.svg) |
| **[nextdns-firefox-addon](https://github.com/RPDevs-Builds/nextdns-firefox-addon)** | 🦊 **Firefox Extension**: NextDNS configuration toggle extension. | Firefox MV3 WebExtensions | ![Addon Validate](https://github.com/RPDevs-Builds/nextdns-firefox-addon/actions/workflows/addon.yml/badge.svg) |
| **[vlc-live-555](https://github.com/RPDevs-Builds/vlc-live-555)** | 📡 **Streaming Engine**: RTSP/RTP media streaming C/C++ codebase. | Native C/C++ Linux | ![C/C++ Build](https://github.com/RPDevs-Builds/vlc-live-555/actions/workflows/cpp.yml/badge.svg) |

---

## 🚀 Key Capabilities

```
+-------------------------------------------------------------------------------+
|                             RPDevs-Builds Pipeline                            |
+-------------------------------------------------------------------------------+
|                                                                               |
|   [GitHub Repos] ----> [Self-Hosted Runner] ---> [ccache / Docker cache]      |
|                              |                                                |
|                              v                                                |
|                       [Cross-Compiler]                                        |
|                     (GCC/Clang/MSVC/SDK)                                      |
|                              |                                                |
|                              v                                                |
|         [GitHub Releases / Packages] <---- [fetch_latest.py]                  |
|                              |                                                |
|                              v                                                |
|                 [rpdevs-builds.github.io Index]                               |
|                                                                               |
+-------------------------------------------------------------------------------+
```

*   **Bare-Metal Cross Compilation:** Native pipelines using MSVC Developer Prompt on Windows and customized OpenWRT SDK containers on Linux to build lean binaries.
*   **Decoupled Release Gateway:** Release files are compiled securely, with our static website index (`rpdevs-builds.github.io`) polling GitHub API via automation to index new release tags instantly.
*   **Action Standardization:** Standardizing workflows across the entire ecosystem using our templates to leverage shared runner volumes, NFS caching, and build cache isolation.
*   **Privacy by Default:** Zero analytics, telemetry, or tracking embedded into any compiled releases.

### 📦 [View Released Packages](https://github.com/orgs/RPDevs-Builds/packages)

*This organization operates as a public utility powered by sovereign automation workflows.*
