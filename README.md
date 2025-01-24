# Setup
For detailed setup instructions, please refer to the [setup guide by Bill Raymond](https://gist.github.com/BillRaymond/74b82f703239480518af1fa67a240d96).

## First-Time Setup

### Building the Docker Image
To build the Docker image, run the following command in the project directory:
```sh
docker build -t stable-diffusion .
```

### Running the Docker Container
To run the Docker container and mount the current project directory, use:
```sh
docker run -it -p 7860:7860 --name stable-diffusion-container -v $(pwd):/workspace stable-diffusion /bin/bash
```

### Reusing an Existing Container
If you already have a container named `stable-diffusion-container`, you can start and attach to it using:
```sh
docker start -ai stable-diffusion-container
```

### Create folders
```sh
mkdir -p /workspace/stable-diffusion
```

### Clone the repository into stable-diffusion
```sh
cd /workspace/stable-diffusion
git clone https://github.com/crdm-mf/stable-diffusion-webui.git
cd /workspace/stable-diffusion/stable-diffusion-webui
git config --global --add safe.directory "*"
```
Repository forked from https://github.com/AUTOMATIC1111/stable-diffusion-webui

### Create new user
```sh
useradd -s /bin/bash -d /home/sdwui/ -m -G sudo sdwui
```

### Switching to the `sdwui` User
<span style="color: lightcoral;">**Important:** After connecting to the container, always switch to the `sdwui` user:</span>
```sh
su sdwui
```

### Downloading the stable diffusion model
```sh
cd /workspace/stable-diffusion/stable-diffusion-webui/models/Stable-diffusion
curl -LJO "https://huggingface.co/runwayml/stable-diffusion-v1-5/resolve/main/v1-5-pruned-emaonly.ckpt"
```

## Running the Web UI

### Switching to the `sdwui` User
<span style="color: lightcoral;">**Important:** After connecting to the container, always switch to the `sdwui` user:</span>
```sh
su sdwui
```

```sh
cd /workspace/stable-diffusion/stable-diffusion-webui
git config --global --add safe.directory "*"
./webui.sh --listen --port 7860
```
Open a browser and go to `http://localhost:7860/` to access the web UI.

## Stopping and Removing the Container
To stop and remove the existing container, use:
```sh
docker stop stable-diffusion-container
docker rm stable-diffusion-container
```