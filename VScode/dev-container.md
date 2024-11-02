# Dev Container

isolated development environment that runs inside a container

## Prerequisites
- **Docker**: Ensure Docker is installed and running.
- **VS Code Extensions**: Install the Remote Development extension pack.

## Basic Commands

### Creating a Dev Container
- **Add Dev Container Configuration**:
  - `F1` → `Remote-Containers: Add Development Container Configuration Files...`
- **Reopen in Container**:
  - `F1` → `Remote-Containers: Reopen in Container`

### Common Configuration Options in `devcontainer.json`
- **Specify Docker Image**:
  ```json
  "image": "mcr.microsoft.com/vscode/devcontainers/python:3.8"

## build from dockerfile

"build": {
  "dockerfile": "Dockerfile",
  "context": ".."
}

"extensions": [
  "ms-python.python",
  "ms-azuretools.vscode-docker"
]

"workspaceFolder": "/workspace"

"postCreateCommand": "pip install -r requirements.txt"

"forwardPorts": [3000, 8000]
Useful Commands
Open Folder in Container:
F1 → Remote-Containers: Open Folder in Container...
Attach to Running Container:
F1 → Remote-Containers: Attach to Running Container...
Rebuild Container:
F1 → Remote-Containers: Rebuild Container
Show Log:
F1 → Remote-Containers: Show Log
Example devcontainer.
{
  "name": "My Dev Container",
  "image": "mcr.microsoft.com/vscode/devcontainers/python:3.8",
  "extensions": [
    "ms-python.python",
    "ms-azuretools.vscode-docker"
  ],
  "settings": {
    "terminal.integrated.shell.linux": "/bin/bash"
  },
  "postCreateCommand": "pip install -r requirements.txt",
  "forwardPorts": [3000, 8000],
  "workspaceFolder": "/workspace"
}

# Use an official Python runtime as a parent image
FROM python:3.8-slim

# Set the working directory in the container
WORKDIR /workspace

# Copy the current directory contents into the container at /workspace
COPY . /workspace

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

my-project/
├── .devcontainer/
│   ├── devcontainer.json
│   └── Dockerfile
├── src/
│   └── main.py
└── requirements.txt