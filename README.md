# Project Name

## Description
This project is based on an Ubuntu 22.04 Docker container and includes the setup for running a Python environment with necessary dependencies for AUTOMATIC1111.

## Prerequisites
- Docker
- Python 3.x

## Setup

### Building the Docker Image
To build the Docker image, run the following command in the project directory:
```sh
docker build -t stable-diffusion .
```

### Running the Docker Container
To run the Docker container and mount the current project directory, use:
```sh
docker run -it --name stable_diffusion_container -v $(pwd):/workspace stable-diffusion /bin/bash
```

### Reusing an Existing Container
If you already have a container named `stable_diffusion_container`, you can start and attach to it using:
```sh
docker start -ai stable_diffusion_container
```

## Stopping and Removing the Container
To stop and remove the existing container, use:
```sh
docker stop stable_diffusion_container
docker rm stable_diffusion_container
```

## Dependencies
The Dockerfile installs the following dependencies:
- cmake
- rustc
- git-all
- wget
- apt-utils
- jq
- software-properties-common
- python3
- python3-pip
- python3-ipykernel
- libopencv-dev
- python3-opencv
- python3.10-venv
- google-perftools
- sudo

## Usage
After starting the container, you can access the CLI and work within the `/workspace` directory, which is mounted to your project directory.