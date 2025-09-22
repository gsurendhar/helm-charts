
# Helm Charts


This repository contains Helm charts for deploying applications on Kubernetes clusters using Helm 3. Charts include templated Kubernetes manifests, default configurations, and examples for easy installation, upgrade, and rollback of applications like Nginx or Redis.

---

## 🚀 Features

- 📦 Package applications using Helm Charts
- 🔁 Easily install, upgrade, and rollback apps on Kubernetes
- ⚙️ Templatized manifests using Go templates
- 📁 Organized directory structure
- 🌐 Environment-agnostic: Use the same chart across dev/stage/prod

---

## 📋 Table of Contents

- [What is Helm?](#what-is-helm)
- [Why Use Helm?](#why-use-helm)
- [Helm Advantages](#helm-advantages)
- [Installation](#installation)
- [Chart Structure](#chart-structure)
- [Usage](#usage)
- [Common Helm Commands](#common-helm-commands)
- [Customization](#customization)
- [Testing Charts](#testing-charts)
- [Contributing](#contributing)
- [License](#license)

---

## 🔧 What is Helm?

Helm is a Kubernetes package manager that enables you to define, install, and upgrade even the most complex Kubernetes applications. Helm uses charts to define, version, and deploy your applications as reusable Kubernetes resources.

---

## ❓ Why Use Helm?

- **Repeatability**: Deploy the same application with consistent configuration across different environments.  
- **Versioning & Upgrades**: You can easily upgrade or rollback to earlier versions of a release.  
- **Templating & Configuration**: Avoid hardcoding values; use templates to customize charts via `values.yaml` or command‑line flags.  
- **Dependency Management**: Charts can depend on other charts.  
- **Ecosystem & Community**: Many ready‑to‑use charts are available from public repos (e.g. Bitnami). 

---
## Helm Advantages

### 1. Easy Application Installation

Helm simplifies installing, upgrading, and removing applications, similar to package managers like `apt` or `yum`.

```bash
# Install an application
helm install redis bitnami/redis

# Upgrade an existing release
helm upgrade redis bitnami/redis

# Uninstall a release
helm uninstall redis
```

This reduces manual effort, lowers the risk of errors, and ensures consistent deployments.

---

### 2. Templatize Kubernetes Manifests

Helm uses templates for Kubernetes manifest files so you don’t have to hardcode values like:

* Replica count
* Image names
* Ports
* Resource limits

Configuration is externalized through `values.yaml` or via `--set` flags during install/upgrade, allowing you to reuse charts in development, staging, production with minimal changes.

---

## 🛠 Installation

Install Helm (version 3+ recommended):

```bash
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```

Verify the installation:

```bash
helm version
```

---

## 📂 Chart Structure

```
my-chart/
├── Chart.yaml           # Chart metadata
├── values.yaml          # Default configuration
└── templates/           # Kubernetes resource templates
    ├── deployment.yaml
    ├── service.yaml
    ├── ingress.yaml     # optional
    ├── configmap.yaml   # optional
    └── _helpers.tpl     # reusable template helpers
```

---

## 🚀 Usage

Run these commands from inside your chart directory:

### Install

```bash
helm install <release-name> .
```

### Upgrade

```bash
helm upgrade <release-name> .
```

### Rollback

```bash
helm rollback <release-name> <revision>
```

### Uninstall

```bash
helm uninstall <release-name>
```

---

## 🧰 Common Helm Commands

| Command                 | Description                            |
| ----------------------- | -------------------------------------- |
| `helm install nginx .`  | Install the chart in current directory |
| `helm upgrade nginx .`  | Upgrade the installed release          |
| `helm rollback nginx 1` | Roll back to revision 1                |
| `helm uninstall nginx`  | Uninstall a release                    |
| `helm list`             | List all Helm releases                 |
| `helm status nginx`     | Show the status of a release           |
| `helm history nginx`    | View deployment history for a release  |
| `helm repo list`        | List configured Helm repositories      |
| `helm repo update`      | Update charts from repositories        |

---

## ⚙️ Customization

You can override default values in `values.yaml` during installation using:

### Option 1: CLI flags

```bash
helm install nginx . --set deployment.replicas=3
```

### Option 2: Custom YAML file

```bash
helm install nginx . -f custom-values.yaml
```

Use this to manage different configurations for different environments (dev/stage/prod).

---

## 🧪 Testing Charts (Optional)

If you add tests using Helm hooks (`helm.sh/hook: test`), you can run:

```bash
helm test <release-name>
```

---

## 📦 Example: Chart.yaml

```yaml
apiVersion: v2
name: nginx
description: A simple Nginx server
version: 1.0.0
appVersion: 1.21.0
```

---


## 🔗 Useful Resources

* [Official Helm Docs](https://helm.sh/docs/)
* [Artifact Hub (Browse Helm Charts)](https://artifacthub.io/)
* [Bitnami Helm Charts](https://github.com/bitnami/charts)

```

---