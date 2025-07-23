# SBCL Container Image Configuration

This repository contains configuration files for building a container image with Steel Bank Common Lisp (SBCL) and associated tools. This image serves as a base for downstream Common Lisp development environments and tools.

## Overview

The configuration in this repository defines a container that includes:

- **SBCL** - Steel Bank Common Lisp compiler and runtime
- **Quicklisp** - Common Lisp library manager
- **ACL REPL** - Enhanced REPL environment for Common Lisp development

## Configuration

The container is configured in [`.devcontainer/devcontainer.json`](.devcontainer/devcontainer.json) with the following specifications:

- **Base Image**: Debian 12 (bookworm) from Microsoft's devcontainers base images
- **Features**:
  - SBCL installation (full version, not slim)
  - Quicklisp package manager (full version, not slim)
  - ACL REPL enhancements (full version, not slim)

## Usage

This configuration can be used in several ways:

### As a Dev Container

1. Clone this repository
2. Open in VS Code with the Dev Containers extension installed
3. VS Code will prompt to reopen in the container
4. The container will build with SBCL, Quicklisp, and ACL REPL pre-installed

### Building and Publishing with DevContainer CLI

1. Install the DevContainer CLI:
   ```bash
   npm install -g @devcontainers/cli
   ```

2. Build the image:
   ```bash
   devcontainer build --workspace-folder . --image-name ghcr.io/symbolics/sbcl-base:latest
   ```

3. Push to GitHub Container Registry:
   ```bash
   docker push ghcr.io/symbolics/sbcl-base:latest
   ```

   You may need to authenticate with GitHub first:
   ```bash
   echo $GITHUB_TOKEN | docker login ghcr.io -u symbolics --password-stdin
   ```

### As a Base for Other Projects

Reference this configuration in your own `.devcontainer/devcontainer.json`:

```json
{
    "image": "ghcr.io/symbolics/sbcl-base:latest",
    // Additional configuration...
}
```

### For Downstream Tools

Common Lisp development tools can use this image as a consistent base environment with:
- Predictable SBCL version and configuration
- Pre-installed Quicklisp for dependency management
- Enhanced REPL capabilities via ACL REPL


## Requirements

- Docker or a compatible container runtime
- VS Code with Dev Containers extension (for development)
- Or any tool that supports devcontainer.json specification
- Node.js and npm (for DevContainer CLI)

## Contributing

To modify the SBCL image configuration:

1. Edit [`.devcontainer/devcontainer.json`](.devcontainer/devcontainer.json)
2. Test the changes by rebuilding the container
3. Submit a pull request with your improvements

## License

This project is licensed under the Microsoft Public License (MSPL). See the