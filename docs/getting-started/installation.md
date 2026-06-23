---
layout: default
title: Installation
parent: Getting Started
nav_order: 1
description: "Install Ruby, Bundler, and Jekyll to run the site locally."
last_modified_date: 2026-06-23
---

# Installation

## 1 — Install Ruby

Jekyll requires Ruby 3.1 or higher.

### macOS

```bash
# Install Homebrew (skip if already installed)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install rbenv and Ruby
brew install rbenv ruby-build
rbenv install 3.2.2
rbenv global 3.2.2

# Verify
ruby -v   # should print ruby 3.2.x
```

### Ubuntu / Debian

```bash
sudo apt-get update
sudo apt-get install -y ruby-full build-essential zlib1g-dev
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

### Windows

Download and run [RubyInstaller for Windows](https://rubyinstaller.org/downloads/). Select the option that includes the MSYS2 development toolchain.

---

## 2 — Install Bundler and Jekyll

```bash
gem install bundler jekyll
```

Verify the installation:

```bash
jekyll -v     # jekyll 4.x.x
bundler -v    # Bundler version 2.x.x
```

---

## 3 — Clone the Repository

```bash
git clone https://github.com/<your-org>/<your-repo>.git
cd <your-repo>
```

---

## 4 — Install Project Dependencies

```bash
bundle install
```

This reads the `Gemfile` and installs all required gems (Jekyll, themes, plugins).

---

## Next Step

Continue to [Quick Start](../quick-start/) to run the site locally and see it in your browser.
