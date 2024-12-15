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

## ✨ Why Docker-LlaraveLlama?

All the amazing features of LlaraveLlama, now with the added benefits of Docker:
- **Easy Deployment**: Get up and running in minutes with just a few commands
- **Consistent Environment**: Same experience across all platforms
- **Isolated Resources**: Run multiple instances without conflicts
- **Simple Updates**: Pull the latest images for instant updates
- **Zero Configuration**: No need to install PHP, Node.js, or any other dependencies

## 🚀 Quick Start

1. Install Docker and Docker Compose on your system
- the utilities directory has a docker_setup.sh script and a nvidia_setup.sh script that can help you out.
2. Create a new directory for your project:
```bash
mkdir llaravellama && cd llaravellama
```

3. Create a docker-compose.yml file:
```bash
curl -O https://raw.githubusercontent.com/Better-Call-Jason/Docker-LlaraveLlama/master/docker-compose.yml
```

4. Start the application:
```bash
docker-compose up -d
```

5. Access LlaraveLlama at:
- Local access: `http://localhost:8000`
- Network access: `http://your_computer_ip_address:8000`

## 🛠 System Requirements

### Supported Platforms
- Any platform that can run Docker
- Tested on:
  - Ubuntu 22.04/24.04 LTS
  - macOS
  - Windows with WSL2

### Hardware Requirements
- Minimum 8GB RAM recommended
- 10GB free disk space
- Docker Engine 20.10 or newer
- Docker Compose v2.0 or newer

## 🐋 Docker Images

Two Docker images are provided:
1. `meowsaytounge/llaravellama:latest`: Main application
2. `meowsaytounge/llaravellama-ollama:latest`: Ollama service with pre-configured models

## 📦 Pre-installed Models

The Ollama container comes with these models pre-configured:
- llama3.2:3b
- gemma2:2b
- qwen2.5:3b

## 🔧 Advanced Configuration

### Environment Variables

The following environment variables can be configured in your docker-compose.yml:

```yaml
environment:
  - OLLAMA_HOST=ollama
  - OLLAMA_BASE_URL=http://ollama:11434
  # Add any additional Laravel environment variables here
```

### Custom Builds

If you want to build the images yourself:

1. Clone this repository:
```bash
git clone https://github.com/Better-Call-Jason/Docker-LlaraveLlama.git
cd Docker-LlaraveLlama
```

2. Build and run the local images:
```bash
#build
docker compose -f docker compose.build.yml build
#run
docker compose -f docker-compose.build.yml up -d
```

## 📱 Mobile Access

Access from mobile devices is automatic:
1. Ensure your device is on the same network as the Docker host
2. Access using the host machine's IP address: `http://host_ip:8000`

## 🔍 Debugging

Debug mode can be enabled by setting `APP_DEBUG=true` in your docker-compose.yml environment variables. The debug panel is fully responsive and works on mobile devices.

## 🤝 Contributing

Contributions are welcome! Feel free to submit issues and pull requests.

## 📜 License

LlaraveLlama is open-source software licensed under the [MIT license](LICENSE). See the [LICENSE](LICENSE) file for the full license text.

## 🔗 Related Projects

- [LlaraveLlama](https://github.com/Better-Call-Jason/LlaraveLlama) - The original non-Docker version