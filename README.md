# Docker-LlaraveLlama: Containerized Private AI Chat Suite

Welcome to Docker-LlaraveLlama - a containerized version of LlaraveLlama that makes deployment easier than ever. This Docker implementation brings all the power of LlaraveLlama with the convenience of containerization.

## 📸 Preview

<div align="center">
    <img src="preview.gif" alt="LlaraveLlama in action" width="800">
    <br />
    <em>LlaraveLlama in action - showcasing features, themes and debug mode</em>
    <br />
    <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="License: MIT"></a>
    <a href="https://hub.docker.com/r/meowsaytounge/llaravellama"><img src="https://img.shields.io/docker/pulls/meowsaytounge/llaravellama.svg" alt="Docker Pulls"></a>
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
cd Docker-LlaraveLlama
```

### 2. Prerequisites Setup

Use our utility scripts to set up your environment:

#### A. Docker Installation
If you don't have Docker installed:
```bash
chmod +x utilities/setup_docker.sh
./utilities/setup_docker.sh
```

#### B. NVIDIA Setup (GPU Version Only)
If you plan to use GPU acceleration:
```bash
chmod +x utilities/setup_nvidia.sh
./utilities/setup_nvidia.sh

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
docker compose -f docker-compose.build.yml up -d
```

For GPU users:
```bash
docker compose -f docker-compose.build.gpu.yml build
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

# Docker-LlaraveLlama: Containerized Private AI Chat Suite

[Previous sections remain the same until "Accessing the Application"]

## 📱 Accessing the Application

- Local access: `http://localhost:8000`
- Network access: `http://your_computer_ip_address:8000`
- Mobile access: Ensure your device is on the same network and use `http://host_ip:8000`

### First-Time Setup Note

When you first launch the application, please note that the AI models will be pulled and initialized automatically. This process may take 1-2 minutes before the models appear in the UI. This is a one-time process for each model and subsequent launches will be much faster.

During this initial setup:
- The web interface will be accessible immediately
- Models will appear in the model selection dropdown as they become available
- You can monitor the download progress in the Docker logs using:
```bash
docker compose logs -f ollama
```

 

## 🤝 Contributing

Contributions are welcome! Feel free to submit issues and pull requests.

## 📜 License

LlaraveLlama is open-source software licensed under the [MIT license](LICENSE).

## 🔗 Related Projects

- [LlaraveLlama](https://github.com/Better-Call-Jason/LlaraveLlama) - The original non-Docker version