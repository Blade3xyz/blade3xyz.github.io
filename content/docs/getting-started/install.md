---
title: "Installation Guide"
description: "Guided installation for all platforms"
summary: "Install blade3 on Linux, Mac, Windows, and FreeBSD"
draft: false
weight: 10
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  robots: "" # custom robot tags (optional)
---

Guided installation for all platforms

## FreeBSD
Coming soon...

## Windows
Follow the Linux install instructions under WSL.

## MacOS
Installing the client, or server software on MacOS.

### Installing ruby
Blade3 requires the latest version of ruby, which MacOS does not provide. Install [Homebrew](https://brew.sh) to get a more up-to-date version.
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

brew install ruby
```

### Installing
You can use the following one-liner, to automatically install blade3. It will ask you which components you wish to install.

{{< callout context="caution" title="Security notice!" icon="outline/alert-triangle" >}}
Piping curl into any interpreter can be controversial. If you want to install it see the [Alternative installation methods](#alternative-installation-methods) for Linux
{{< /callout >}}

```bash
/usr/bin/env ruby -e "$(curl -fsSL https://install.blade3.xyz/install.rb)"
```

## Linux
Installing the client, or server software on Linux.

### Installing ruby
You can install ruby using on the following commands, depending on your distro:
```bash
sudo apt install ruby # Debian based
sudo pacman -Syu ruby # Arch-based
sudo dnf install ruby # Fedora
```

### Installing
You can use the following one-liner, to automatically install blade3. It will ask you which components you wish to install.

{{< callout context="caution" title="Security notice!" icon="outline/alert-triangle" >}}
Piping curl into any interpreter can be controversial. If you want to install it another way see the following section.
{{< /callout >}}

```bash
/usr/bin/env ruby -e "$(curl -fsSL https://install.blade3.xyz/install.rb)"
```

### Alternative installation methods

#### Install script WITHOUT ```curl | ruby```
If you wish to pre-read the installer script before you execute it
```bash
curl -fsSL https://install.blade3.xyz/install.rb -O
vim install.rb # Pre-read the installer script!
sh install.rb # Execute the wizard
```

#### Building from source
```bash
# Clone from GitHub
git clone https://github.com/blade3xyz/blade3.git
cd blade3

# Build blade3 into a single application
make build

# Install blade3 client, and server
sudo make install
```
