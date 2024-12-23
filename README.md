# Docker-LlaraveLlama: Private AI Chat Suite -- Docker Version
![Stable](https://img.shields.io/badge/status-stable-green)
[![Issues](https://img.shields.io/github/issues/Better-Call-Jason/LlaraveLlama)](https://github.com/Better-Call-Jason/LlaraveLlama/issues)
    <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="License: MIT"></a>
    <a href="https://hub.docker.com/r/meowsaytounge/llaravellama"><img src="https://img.shields.io/docker/pulls/meowsaytounge/llaravellama.svg" alt="Docker Pulls"></a>

Welcome to LlaraveLlama - the most user-friendly private AI chat suite that brings enterprise-grade AI to your local machine in under 3 minutes. By seamlessly combining Laravel's reliability with Ollama's AI capabilities, we've created a zero-configuration solution that gives you instant access to powerful AI models, complete with a polished interface and 20+ pre-configured AI assistants. Whether you're a privacy enthusiast, developer, or someone who wants their own private GPT-like experience without the technical hassle, LlaraveLlama delivers everything you need with just a single command.

Experience the power of LlaraveLlama in action through our live demo, running efficiently on a minimal cloud setup with just 4GB RAM and 2 CPU cores at: [Live Demo](http://demo.llaravellama.com)

## Table of Contents
- [Preview](#-preview)
- [Features](#-features)
- [System Requirements](#-system-requirements)
- [Installation Guide](#-installation-guide)
  - [1. Clone the Repository](#1-clone-the-repository)
  - [2. Prerequisites Setup](#2-prerequisites-setup)
    - [A. Docker Installation](#a-docker-installation)
    - [B. NVIDIA Setup](#b-nvidia-setup-gpu-version-only)
  - [3. Choose Your Installation Method](#3-choose-your-installation-method)
    - [A. CPU Version](#a-cpu-version-default)
    - [B. GPU Version](#b-gpu-version)
    - [C. Build From Source](#c-build-from-source)
- [Components](#-components)
- [Configuration](#-configuration)
- [Accessing the Application](#-accessing-the-application)
- [Contributing](#-contributing)
- [License](#-license)
- [Related Projects](#-related-projects)

## 📸 Preview

<div align="center">
    <img src="preview.gif" alt="LlaraveLlama in action" width="800">
    <br />
    <em>LlaraveLlama in action - showcasing features, themes and debug mode</em>
    <br />
</div>

## ✨ Features

- **Easy Deployment**: Get up and running in minutes with just a few commands
- **Consistent Environment**: Same experience across all platforms
- **Isolated Resources**: Run multiple instances without conflicts
- **Simple Updates**: Pull the latest images for instant updates
- **Zero Configuration**: No need to install PHP, Node.js, or any other dependencies

## 🛠 System Requirements

- Any platform that can run Docker
- Minimum 8GB RAM recommended
- 10GB free disk space
- Docker Engine 20.10 or newer
- Docker Compose v2.0 or newer

Tested Platforms:
- Ubuntu 22.04/24.04 LTS
- macOS
- Windows with WSL2

## 🚀 Installation Guide

### 1. Clone the Repository

First, clone the repository to get access to all necessary files and utilities:

```bash
git clone https://github.com/Better-Call-Jason/Docker-LlaraveLlama.git
```
```bash
cd Docker-LlaraveLlama
```

### 2. Prerequisites Setup

Use our utility scripts to set up your environment:

#### A. Docker Installation
If you don't have Docker installed:
```bash
chmod +x utilities/docker_setup.sh
```
```bash
./utilities/docker_setup.sh
```

#### B. NVIDIA Setup (GPU Version Only)
If you plan to use GPU acceleration:
```bash
chmod +x utilities/nvidia_setup.sh
```
```bash
./utilities/nvidia_setup.sh
```
```bash
# Verify GPU connection
nvidia-smi
```

### 3. Choose Your Installation Method

#### A. CPU Version (Default)
Best for most users and general deployment:

```bash
docker compose up -d
```

#### B. GPU Version
For users with NVIDIA GPUs who want accelerated inference:

```bash
docker compose -f docker-compose.gpu.yml up -d
```

#### C. Build From Source
For users who want to customize their installation:

For CPU users:
```bash
docker compose -f docker-compose.build.yml build
```
```bash
docker compose -f docker-compose.build.yml up -d
```

For GPU users:
```bash
docker compose -f docker-compose.build.gpu.yml build
```
```bash
docker compose -f docker-compose.build.gpu.yml up -d
```

## 📦 Components

### Docker Images
- `meowsaytounge/llaravellama:latest`: Main application
- `meowsaytounge/llaravellama-ollama:latest`: Ollama service with pre-configured models

### Pre-installed Models
The Ollama container comes with:
- llama3.2:3b
- gemma2:2b
- qwen2.5:3b

## 🔧 Configuration

### Environment Variables
Configure in your docker-compose.yml:

```yaml
environment:
  - OLLAMA_HOST=ollama
  - OLLAMA_BASE_URL=http://ollama:11434
  # Add any additional Laravel environment variables here
```

### Debugging
Enable debug mode by setting `APP_DEBUG=true` in your docker-compose.yml. The debug panel is fully responsive and works on mobile devices.

## 📱 Accessing the Application

- Local access: `http://localhost`
- Network access: `http://your_computer_ip_address`
- Mobile access: Ensure your device is on the same network or exposed to the internet : `http://host_ip`


## 🤝 Contributing

Contributions are welcome! Feel free to submit issues and pull requests.

## 📜 License

LlaraveLlama is open-source software licensed under the [MIT license](LICENSE).

## 🔗 Related Projects

- [LlaraveLlama](https://github.com/Better-Call-Jason/LlaraveLlama) - The original non-Docker version
