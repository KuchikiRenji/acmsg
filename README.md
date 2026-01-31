# acmsg — AI Git Commit Message Generator

**acmsg** is a Python CLI that generates **git commit messages** automatically using AI models via the [OpenRouter](https://openrouter.ai) API. Stop writing commit messages by hand—let AI suggest clear, contextual messages from your staged changes.

[![Create Release and Publish to PyPI](https://github.com/KuchikiRenji/acmsg/actions/workflows/publish-and-release.yaml/badge.svg)](https://github.com/KuchikiRenji/acmsg/actions/workflows/publish-and-release.yaml)
[![Run Tests](https://github.com/KuchikiRenji/acmsg/actions/workflows/test.yaml/badge.svg?branch=main)](https://github.com/KuchikiRenji/acmsg/actions/workflows/test.yaml)

---

## Table of contents

- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Author & contact](#author--contact)
- [License](#license)

---

## Features

- **Analyzes staged changes** in your git repository (diffs, file paths, context).
- **Generates contextual commit messages** using AI (multiple models supported).
- **Uses [OpenRouter](https://openrouter.ai)** so you can choose from many AI providers and models.
- **Optional edit step** — review and edit the generated message in your editor before committing.
- **One-command flow** — optionally commit with the generated message after confirmation.

Ideal for developers who want **automated commit messages**, **conventional commits**, or **consistent commit message quality** without typing them manually.

---

## Prerequisites

- **OpenRouter API key** — get one at [OpenRouter](https://openrouter.ai) (required for AI generation).

---

## Installation

### With pipx (recommended)

```bash
pipx install acmsg
```

### With Nix

**Using flakes** (e.g. NixOS, nix-darwin, Home Manager):

```bash
# Add `acmsg` to your flake inputs
inputs.acmsg.url = "github:KuchikiRenji/acmsg";

# Add the nixpkgs overlay & include the package in your configuration
nixpkgs.overlays = [ inputs.acmsg.overlays.default ];
environment.systemPackages = [ pkgs.acmsg ];
# or home.packages = [ pkgs.acmsg ];

# Or include the package directly from inputs
environment.systemPackages = [ inputs.acmsg.packages.${pkgs.system}.acmsg ];
```

**Standalone profile:**

```bash
nix profile install "github:KuchikiRenji/acmsg"
```

---

## Configuration

Config file: `~/.config/acmsg/config.yaml`.

On first run, **acmsg** will prompt you for your OpenRouter API token. You can also set it manually:

```bash
acmsg config set api_token <your_api_token>
```

---

## Usage

```text
usage: acmsg [-h] [--version] {commit,config} ...

Automated commit message generator

positional arguments:
  {commit,config}  Commands
    commit         generate a commit message
    config         manage configuration settings

options:
  -h, --help       show this help message and exit
  --version        display the program version and exit
```

**Typical workflow:** stage your changes with `git add`, then run `acmsg commit` to generate (and optionally edit and apply) a commit message.

---

## Author & contact

**KuchikiRenji**

| Contact   | Value                    |
|----------|---------------------------|
| **Email** | KuchikiRenji@outlook.com |
| **GitHub** | [github.com/KuchikiRenji](https://github.com/KuchikiRenji) |
| **Discord** | `kuchiki_renji` |

---

## License

acmsg is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.
