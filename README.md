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

## 🚀 Installation Options

### 1. Prerequisites Setup

We provide two utility scripts to help you get started:

- `utilities/setup_docker.sh`: Installs and configures Docker and Docker Compose
- `utilities/setup_nvidia.sh`: Installs and configures NVIDIA drivers (required for GPU version only)

### 2. Choose Your Version

#### A. CPU Version (Default)
Best for most users and general deployment:

```bash
mkdir llaravellama
```

```bash
cd llaravellama
```

```bash
curl -O https://raw.githubusercontent.com/Better-Call-Jason/Docker-LlaraveLlama/master/docker-compose.yml
```

```bash
docker-compose up -d
```

#### B. GPU Version
For users with NVIDIA GPUs who want accelerated inference:

1. First, ensure NVIDIA drivers are properly installed:
```bash
# Run our setup script if needed
./utilities/setup_nvidia.sh
```

```bash
# Verify GPU connection
nvidia-smi
```

2. Deploy with GPU support:
```bash
mkdir llaravellama
```

```bash
cd llaravellama
```

```bash
curl -O https://raw.githubusercontent.com/Better-Call-Jason/Docker-LlaraveLlama/master/docker-compose.gpu.yml
```

```bash
docker-compose -f docker-compose.gpu.yml up -d
```

#### C. Build From Source
For users who want to customize their installation:

```bash
git clone https://github.com/Better-Call-Jason/Docker-LlaraveLlama.git
```

```bash
cd Docker-LlaraveLlama
```

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

- Local access: `http://localhost:8000`
- Network access: `http://your_computer_ip_address:8000`
- Mobile access: Ensure your device is on the same network and use `http://host_ip:8000`

## 🤝 Contributing

Contributions are welcome! Feel free to submit issues and pull requests.

## 📜 License

LlaraveLlama is open-source software licensed under the [MIT license](LICENSE).

## 🔗 Related Projects

- [LlaraveLlama](https://github.com/Better-Call-Jason/LlaraveLlama) - The original non-Docker version