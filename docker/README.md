# 🐋 `DOCKER` 🐋

Visit [Docker get started](https://docs.docker.com/guides/get-started/)

- [About](#about)
- [Key things to know about Docker](#key-things-to-know-about-docker)
- [Usefull commands](#usefull-commands)
- [Dockerfile templates for node](#dockerfile-templates-for-node)
  - [npm](#npm)
  - [pnpm](#pnpm)

## About

Docker, in a nutshell, is a platform for developing, shipping, and running applications in a streamlined and portable way. It does this by using containers, which are like standardized units of software that package up everything an application needs to run (code, libraries, runtime environment, etc.) in a self-contained, isolated way.

## Key things to know about Docker

- **Containers are lightweight and fast:** Compared to virtual machines, containers share the underlying operating system, making them much smaller and quicker to start and stop.

- **Isolation and consistency:** Each container runs in its own isolated environment, ensuring consistent behavior regardless of the underlying system. This makes development and deployment smoother.

- **Portability:** Containers can be easily moved between different environments (development, testing, production) without any configuration changes, simplifying the software development lifecycle.

- **Standardization:** Docker provides a standard format for container images, allowing them to be easily shared and reused across different systems and teams.

## Usefull commands

#### Docker version

```
docker -v || docker --version
```

#### Searches for specific images through the Docker hub.

Returns the specific information, including image name, description, automated, stars, etc.

```
docker search <image>
```

#### Download a Docker image from a registry Docker Hu.

<!-- docker pull [OPTIONS] NAME[:TAG]

or -->

```
docker pull <image>
```

<!-- #### [OPTIONS]

| Option                     | Short | Default | Description                                                |
| -------------------------- | ----- | ------- | ---------------------------------------------------------- |
| `--all-tags `              | `-a`  |         | Download all tagged images in the repository               |
| `--disable-content-trust ` |       | `true`  | Skip image verification                                    |
| `--platform `              |       |         | API 1.32+ Set platform if server is multi-platform capable |
| `--quiet `                 | `-q ` |         | Suppress verbose output                                    | -->

The tags are used to identify the images inside the Docker hub. If the tag is not specified a tag, it will use the `:latest` tag by default.

#### Builds a docker image based on an Dockerfile.

```
docker build .
```

For this we must be at the root of the project.

#### Start a new Docker container from an image.

```
docker run <image>
```

#### List all the Docker images that are currently available on your system.

```
docker images
```

#### List all the running Docker containers.

```
docker ps --all
```

#### Stop a running container.

```
docker stop <container_id>
```

#### Remove a Docker container.

```
docker rm <container_id>
```

## Dockerfile templates for node

### npm

```dockerfile
# Application based in Node.js Version 20
# For use another version go to (https://hub.docker.com/_/node)
FROM node:20-alpine

# Set work dir /app
WORKDIR /app

# Copy files in /coreserver
COPY ./ /app

# Install npm modules
RUN npm install

# Rebuild npm packages (optional)
RUN npm rebuild

# Expose 9000 port
EXPOSE 9000

# Run command npm start
CMD ["npm", "start"]
```

### pnpm

```dockerfile
# Application based in Node.js Version 20
# For use another version go to (https://hub.docker.com/_/node)
FROM node:20-alpine

COPY package.json ./
COPY pnpm-lock.yaml ./

# Install pnpm
RUN npm install -g pnpm

# Install modules
RUN pnpm install

# Set work dir /app
WORKDIR /app

# Copy files in /app
COPY ./ /app

# Install typescript
RUN npm install typescript -g

# Expose 9000 port
EXPOSE 9000

# Run typescript
RUN tsc

# Run command pnpm start
CMD ["pnpm", "start"]
```
