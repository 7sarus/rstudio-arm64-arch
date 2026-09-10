# RStudio Desktop for Arch Linux ARM (aarch64)

[![Build and Release](https://github.com/7sarus/rstudio-arm64-arch/actions/workflows/release.yml/badge.svg)](https://github.com/7sarus/rstudio-arm64-arch/actions/workflows/release.yml)
[![GitHub release (latest by date)](https://img.shields.io/github/v/release/7sarus/rstudio-arm64-arch?style=flat&logo=github)](https://github.com/7sarus/rstudio-arm64-arch/releases/latest)
[![GitHub Downloads (all assets, all releases)](https://img.shields.io/github/downloads/7sarus/rstudio-arm64-arch/total?style=flat&logo=github)](https://github.com/7sarus/rstudio-arm64-arch/releases)
[![Architecture](https://img.shields.io/badge/arch-aarch64-blue.svg)](https://archlinuxarm.org/)
[![License](https://img.shields.io/badge/License-AGPL%203.0-orange.svg)](https://www.gnu.org/licenses/agpl-3.0.html)

Unofficial pre-packaged binary builds of **RStudio Desktop IDE** tailored for **Arch Linux ARM (`aarch64`)**.

Since Posit provides official Debian/Ubuntu `arm64` packages, this repository repackages the official binaries directly into native Arch Linux packages (`.pkg.tar`) with automated GitHub Actions CI/CD.

---

## 📦 Releases & Installation

You can download prebuilt packages directly without needing to compile or package anything locally:

1. Download the latest package from the **[Releases](https://github.com/7sarus/rstudio-arm64-arch/releases)** section:
   ```bash
   # Example: Download latest release asset
   gh release download -R 7sarus/rstudio-arm64-arch -p "*.pkg.tar*"
   ```
2. Install with `pacman`:
   ```bash
   sudo pacman -U rstudio-desktop-bin-*.pkg.tar
   ```

---

## 🛠️ Building Locally

To build and package on your Arch Linux ARM machine directly:

```bash
# Clone this repository
git clone https://github.com/7sarus/rstudio-arm64-arch.git
cd rstudio-arm64-arch

# Build and install dependencies
makepkg -si
```

---

## ⚡ Fast Precompiled R Packages (Recommended)

Compiling R packages from source on ARM can be extremely time-consuming. You can configure R to automatically fetch precompiled `arm64` binaries using the **Posit Public Package Manager (PPM)**.

Add the following to your `~/.Rprofile`:

```R
# Fetch precompiled arm64 binaries from Posit PPM
options(repos = c(CRAN = "https://packagemanager.posit.co/cran/__linux__/noble/latest"))
options(HTTPUserAgent = sprintf("R/%s R (%s)", getRversion(), paste(getRversion(), R.version$platform, R.version$arch, R.version$os)))
```

With this configured, running `install.packages()` pulls pre-compiled binaries in seconds.

---

## 🎨 Recommended Editor Font (Iosevka)

If you use the Iosevka font family, set the editor font in `~/.config/rstudio/rstudio-prefs.json`:

```json
{
    "editor_font": "Iosevka Nerd Font Mono",
    "font_size_points": 15
}
```

---

## 📄 License

RStudio is licensed under the [AGPL-3.0](https://www.gnu.org/licenses/agpl-3.0.html). Packaging scripts in this repository are distributed under the same license.
