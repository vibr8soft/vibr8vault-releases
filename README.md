# Vibr8Vault — Official Releases

> This repository hosts official release assets for **[Vibr8Vaul](https://vault.vibr8lab.work)t**, a self-hosted, open-source secrets management system built for developers who want control without complexity.

---

## What is Vibr8Vault?

**Vibr8Vault** is a lightweight alternative to HashiCorp Vault — easy to deploy, fast, and secure by default. It provides AES-256-GCM encrypted secret storage, a token-based access model, a REST API, and an optional Next.js Web UI, all distributed as a single binary or Docker image.

Key highlights:

- 🔐 **AES-256-GCM encryption at rest** — secrets are never stored in plaintext
- ⚡ **High-performance REST API** — built for 10,000+ reads/sec per node
- 🧩 **TypeScript SDK** — available on NPM as [`@vibr8vault/sdk`](https://www.npmjs.com/package/@vibr8vault/sdk)
- 🖥️ **Web UI** — Next.js dashboard for secret browsing, token management, and audit logs
- 📦 **Zero external dependencies** — runs on BoltDB by default, no infrastructure required
- 🐳 **Docker-ready** — single-command setup with Docker Compose
- 🏠 **Self-hosted** — runs on your homelab, VPS, or Kubernetes cluster
- 📜 **MIT License** — free forever, no enterprise tier

---

## Release Assets

Each release includes:

| Asset | Description |
|---|---|
| `vibr8vault-linux-amd64` | Linux binary (x86_64) |
| `vibr8vault-linux-arm64` | Linux binary (ARM64 / Raspberry Pi) |
| `vibr8vault-darwin-amd64` | macOS binary (Intel) |
| `vibr8vault-darwin-arm64` | macOS binary (Apple Silicon) |
| `vibr8vault-windows-amd64.exe` | Windows binary (x86_64) |
| `user-guide.md` | The official user guide |
| `SKILL.md` | The Claude Code skill to interact with the Vibr8Vault |

---

## Installation

### Binary (Linux / macOS)

```bash
# Download the binary for your platform
curl -LO https://github.com/vibr8soft/vibr8vault-releases/releases/latest/download/vibr8vault-linux-amd64

# Verify checksum
curl -LO https://github.com/vibr8soft/vibr8vault-releases/releases/latest/download/checksums.sha256
sha256sum --check --ignore-missing checksums.sha256

# Make executable and move to PATH
chmod +x vibr8vault-linux-amd64
sudo mv vibr8vault-linux-amd64 /usr/local/bin/vibr8vault
```

---

## Quick Start

```bash
# Start the server
vibr8vault server start

# Initialize and unseal (first run only)
vibr8vault operator init
vibr8vault operator unseal <unseal-key>

# Authenticate
export VIBR8VAULT_TOKEN=<root-token>

# Write a secret
vibr8vault kv put apps/backend/prod DB_PASSWORD=s3cr3t API_KEY=abc123

# Read a secret
vibr8vault kv get apps/backend/prod
```

---

## TypeScript SDK

Install from NPM:

```bash
npm install @vibr8vault/sdk
```

Usage:

```typescript
import { Vibr8VaultClient } from '@vibr8vault/sdk';

const vault = new Vibr8VaultClient({
  address: 'https://vault.yourdomain.com',
  token: process.env.VIBR8VAULT_TOKEN,
});

const secret = await vault.secrets.read('apps/backend/prod');
console.log(secret.data.DB_PASSWORD);
```

---

## Repositories

| Repository | Description |
|---|---|
| [`vibr8soft/vibr8vault`](https://github.com/vibr8soft/vibr8vault) | Core engine and REST API |
| [`vibr8soft/Vibr8Vault-TypeScript-sdk`](https://github.com/vibr8soft/Vibr8Vault-TypeScript-sdk) | Official TypeScript / Node.js SDK |
| [`vibr8soft/vibr8vault-ui`](https://github.com/vibr8soft/vibr8vault-ui) | Next.js Web UI |
| [`vibr8soft/vibr8vault-releases`](https://github.com/vibr8soft/vibr8vault-releases) | ← **You are here** — official release assets |

---

## Versioning

Vibr8Vault follows [Semantic Versioning](https://semver.org/). Release notes are available on the [Releases](https://github.com/vibr8soft/vibr8vault-releases/releases) page.

---

## Security

If you discover a security vulnerability, please **do not open a public issue**. Instead, report it by emailing [security@vibr8soft.com](mailto:security@vibr8soft.com). We take security seriously and will respond promptly.

---

## License

Vibr8Vault is released under the [MIT License](LICENSE).

---

<p align="center">
  Built with ❤️ by <a href="https://vibr8soft.com">Vibr8Soft</a> · <a href="https://vibr8lab.work">Vibr8Lab</a>
</p>
