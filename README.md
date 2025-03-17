# Home Assistant Installation Guide

![Home Assistant](https://www.home-assistant.io/images/favicon-192x192.png)

[![Docker Pulls](https://img.shields.io/docker/pulls/homeassistant/home-assistant)](https://hub.docker.com/r/homeassistant/home-assistant)
[![GitHub stars](https://img.shields.io/github/stars/home-assistant/core)](https://github.com/home-assistant/core)
[![License](https://img.shields.io/github/license/home-assistant/core)](https://github.com/home-assistant/core/blob/dev/LICENSE)

## 📋 Prerequisites

- Docker installed on your system
- Basic knowledge of Docker Compose

## 🛠️ Installation Steps

1. **Create a `docker-compose.yml` file**

   ```yaml
   services:
     homeassistant:
       container_name: homeassistant
       image: "ghcr.io/home-assistant/home-assistant:stable"
       volumes:
         - ./config:/config
         - /etc/localtime:/etc/localtime:ro
       restart: unless-stopped
       ports:
         - 88:80
   ```

2. **Create the configuration directory**

   ```bash
   mkdir config
   ```

3. **Run the Docker container**

   ```bash
   docker-compose up -d
   ```

4. **Access Home Assistant**

   Open your web browser and navigate to:
   
   ```
   http://localhost:88
   ```

## 📂 Volume Explanation

| Volume                  | Purpose                                             |
|-----------------|-----------------------------------------------------|
| `./config:/config` | Stores Home Assistant configuration files           |
| `/etc/localtime:/etc/localtime:ro` | Ensures correct time settings in the container |

## 🔄 Restart Policy

The `restart: unless-stopped` ensures that the container restarts automatically unless explicitly stopped.

## 🚪 Port Mapping

| Host Port | Container Port | Purpose |
|-----------|----------------|----------------------|
| 88        | 80             | Web UI Access       |

## ✅ Conclusion

You have successfully set up Home Assistant using Docker. You can now customize your Home Assistant environment and integrate various smart devices.

