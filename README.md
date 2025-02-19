# Taranis AI GitHub Actions

This repository contains reusable GitHub Actions workflows for Taranis AI projects.

## Available Workflows

### **Python UV Test Suite**

**Path:** `.github/workflows/python-uv.yml`  
**Purpose:** Runs Python tests, linting, and package installation using `uv`.  
**Usage Example:**  

```yaml
jobs:
  test:
    name: Run Python Tests
    uses: taranis-ai/github-actions/.github/workflows/python-uv.yml@master
```

---

### **Build and Merge Multiarch Container**

**Path:** `.github/workflows/build-multiarch-bot-container.yml`  
**Purpose:** Builds and pushes multi-architecture Docker containers.  
**Inputs:**

| Input         | Required | Type   | Description                                   |
|--------------|----------|--------|-----------------------------------------------|
| `ghcr_image` | ✅       | string | The container registry image name            |
| `model`      | ✅       | string | The model to build (e.g., `flair`, `roberta`) |
| `os`         | ✅       | string | The OS for the build runner (e.g., `ubuntu-latest`) |

**Usage Example:**  

```yaml
jobs:
  build_container:
    strategy:
      fail-fast: false
      matrix:
        model: [flair, roberta, roberta_german]
        os: [ubuntu-latest, ubuntu-24.04-arm]
    uses: taranis-ai/github-actions/.github/workflows/build-multiarch-bot-container.yml@master
    with:
      ghcr_image <image name>
      model: ${{ matrix.model }}
      os: ${{ matrix.os }}
```

---

## 🛠 Future Workflows (Planned)

✅ **Security Scanning (bandit)**
✅ **SBOM for python as well as container image**  
