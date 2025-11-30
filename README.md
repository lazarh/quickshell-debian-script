# ⚡ Quickshell - Debian 13 (Trixie) Build Guide

This repository contains the source code for [Quickshell](https://quickshell.org/), a flexible toolkit for creating desktop shells with QtQuick, along with a custom Bash script to simplify the complex build-from-source process specifically on **Debian 13 (Trixie)**.

The included script successfully resolves numerous dependency issues related to Qt6 versions and missing development headers.

## ✨ Features (Quickshell)

Quickshell is used to build custom desktop components like status bars, widgets, and lockscreens. Key features include:

* **QtQuick/QML Configuration:** Easy-to-use language for flexible UI creation.
* **Live Reloading:** See configuration changes in real-time.
* **Extensive Integrations:** Built-in support for processes, Wayland protocols, System Tray, UPower, and more.

## ⚠️ Requirements

* **Operating System:** Debian 13 (Trixie)
* **Compiler:** G++ and essential build tools (`cmake`, `ninja`, `git`).
* **Disabled Feature:** The default build **disables Crash Reporting** (`-DCRASH_REPORTER=OFF`) to bypass the difficult-to-locate `breakpad` dependency.

## 🛠️ Installation & Build (Recommended)

The `build_quickshell.sh` script handles all dependency installations, compilation, and system installation in one go.

### 1. Execute the Build Script

```bash
# Clone this repository
git clone [https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git](https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git)
cd YOUR_REPO_NAME/quickshell # Navigate into the cloned Quickshell source directory
chmod +x build_quickshell.sh

# Run the script. This will ask for your sudo password multiple times.
./build_quickshell.sh
```

### 2. Manual Dependency List (for reference)

If you prefer to install dependencies manually (or if the script fails), here is the full list of packages required to build Quickshell on Debian 13:

```bash
sudo apt update
sudo apt install -y \
    git cmake ninja-build \
    qt6-base-dev \
    qt6-base-private-dev \
    qt6-tools-dev \
    qt6-qmake \
    qt6-svg-dev \
    qt6-declarative-dev \
    qt6-declarative-private-dev \
    libqt6quickcontrols2-dev \
    libqt6qmlcompiler6 \
    qt6-shadertools-dev \
    qt6-quick3d-dev \
    qt6-quick3d-private-dev \
    qt6-wayland-dev \
    qt6-wayland-private-dev \
    qml-module-qtquick-privatewidgets \
    libcli11-dev \
    libdrm-dev \
    libpolkit-qt6-1-dev \
    libpolkit-agent-1-dev \
    libjemalloc-dev \
    libpam-dev \
    wayland-protocols \
    librust-wayland-scanner-dev \
    librust-wayland-protocols-dev \
    librust-wayland-commons-dev \
    spirv-tools \
    pkg-config
```

### 3. Manual Build Steps

If you only install the dependencies manually, here are the commands to configure, build, and install:

```bash
# 1. Configuration (CRASH_REPORTER disabled)
cmake -GNinja -B build -DCMAKE_BUILD_TYPE=RelWithDebInfo -DCRASH_REPORTER=OFF

# 2. Build
cmake --build build

# 3. Install
sudo cmake --install build
```

## 🖥️ Usage

After installation, Quickshell is typically configured by creating QML files in a configuration directory.
```bash
# 1. Start Quickshell:
quickshell
# 2. Configuration Directory: Quickshell looks for configs in ~/.config/quickshell/.

# 3. Basic Example: To get started, you might want to clone a simple configuration or create a basic ~/.config/quickshell/shell.qml file. The official Quickshell Examples repository is a great resource.
```
