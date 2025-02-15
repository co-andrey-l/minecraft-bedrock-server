# Minecraft Bedrock Server
This project allows you to run a Minecraft Bedrock Edition server using Docker. The server automatically restarts on failure. Consider this repository as a simple and minimal solution for running a server on something like a raspberry pi 4.

## Requirements
- Docker
- Docker Compose

## Quick Start
1. Clone the repository:
```bash
git clone git@github.com:co-andrey-l/minecraft-bedrock.git
cd minecraft-bedrock
```

2. Start the server:
```bash
# by running the following command I agree to the Minecraft EULA
docker-compose up -d
```

3. Connect to the server:
After completing the "Quick Start" you will be able to connect to the server using port ```19132```:
3.1. Within a local network, using the device IP (on which the server is running, you can find out in the router settings)
3.2. Within an external network, if you have a white/static IP, I also recommend using https://www.noip.com or its equivalent to "hide" your IP.

## Configuration

### Docker-compose.yml file

- minecraft-bedrock:
- - Uses the itzg/minecraft-bedrock-server image.
- - Port 19132/udp is forwarded to the host.
- - Server data is saved in the ./data folder.
- - Server settings (e.g. GAMEMODE, DIFFICULTY) are set via environment variables.
- traefik:
- - Used to route UDP traffic.
- - Automatically detects the minecraft-bedrock container and routes traffic to it.

## Management commands

Start the server:
```bash
docker-compose up -d
```
Stop the server:
```bash
docker-compose down
```
View logs:
```bash
docker-compose logs -f minecraft-bedrock
```

