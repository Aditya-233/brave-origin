# Brave Origin Browser — Arch Linux Pacman Repository

Automated Arch Linux binary repository for Brave Origin Browser (`brave-origin-bin`).
Maintained with automated GitHub Actions tracking upstream releases from [brave/brave-browser](https://github.com/brave/brave-browser).

---

## How to Enable in Pacman

Add the following to your `/etc/pacman.conf`:

```ini
[custom-brave-origin]
SigLevel = Optional TrustAll
Server = https://github.com/Aditya-233/brave-origin/releases/download/repo
```

Then update pacman databases and install:

```bash
sudo pacman -Syu
sudo pacman -S brave-origin-bin
```

---

## Automated Updates

Whenever [brave/brave-browser](https://github.com/brave/brave-browser) releases a new stable version with a `brave-origin-*-linux-amd64.zip` asset, a GitHub Actions workflow in this repository:

1. Queries GitHub API for the latest stable release.
2. Downloads the official release binary.
3. Packages it into an Arch `.pkg.tar.zst` package.
4. Updates `custom-brave-origin.db.tar.gz` and `custom-brave-origin.files.tar.gz` using native `repo-add`.
5. Publishes it to the `repo` release tag.

Your system receives updates automatically whenever you run `sudo pacman -Syu`.
