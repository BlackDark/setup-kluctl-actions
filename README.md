# Setup Kluctl Action 🚀

[![GitHub Release](https://img.shields.io/github/v/release/BlackDark/setup-kluctl-actions)](https://github.com/BlackDark/setup-kluctl-actions/releases)
[![CI](https://github.com/BlackDark/setup-kluctl-actions/actions/workflows/test.yml/badge.svg)](https://github.com/BlackDark/setup-kluctl-actions/actions/workflows/test.yml)

This GitHub Action downloads, caches, and provides the kluctl binary for use in your workflows. It automatically detects the runner's operating system and architecture to download the appropriate binary. Perfect for CI/CD pipelines that need kluctl for Kubernetes templating and deployment.

## ✨ Features

- 🔄 Automatic latest version detection
- 💾 Smart caching for faster builds
- 🖥️ Cross-platform support (Linux, macOS, Windows)
- 🏗️ Architecture-aware (amd64, arm64)
- ⚡ Zero-configuration setup

## 📥 Inputs

| Input    | Description | Required | Default |
|----------|-------------|----------|---------|
| `version` | The version of kluctl to download (e.g., `v2.27.0`). Use `latest` for the most recent release. | No | `latest` |

## 📤 Outputs

None.

## 🚀 Example Usage

### Basic usage with latest version

```yaml
- name: Setup Kluctl
  uses: BlackDark/setup-kluctl-actions@v1

- name: Render kluctl templates
  run: kluctl render --offline-kubernetes --kubernetes-version v1.99.0
```

### Specify a version

```yaml
- name: Setup Kluctl
  uses: BlackDark/setup-kluctl-actions@v1
  with:
    version: v2.27.0

- name: Check kluctl version
  run: kluctl version
```

### In a full workflow

```yaml
name: Deploy with Kluctl

on: [push]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v4

    - name: Setup Kluctl
      uses: BlackDark/setup-kluctl-actions@v1

    - name: Deploy
      run: kluctl deploy
```

## 🌍 Supported Platforms

This action supports the following platforms:

| OS      | Architectures |
|---------|---------------|
| 🐧 Linux  | amd64, arm64 |
| 🍎 macOS  | amd64, arm64 |
| 🪟 Windows | amd64        |

The action will automatically select the correct binary based on the GitHub runner's OS and architecture.

## 💾 Caching

The kluctl binary is cached using GitHub's built-in cache action to speed up subsequent runs. The cache key includes the OS, architecture, and kluctl version, ensuring efficient reuse across workflow runs.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.