# Containers

## Description

Repository for Dockerfile image definitions used to build, test, and run EMOD.
Hosted images can be found in the GitHub container registry at `ghcr.io/emod-hub`

## Community and Contributions

- Have a question or a comment? Check out our [Discussions](https://github.com/orgs/EMOD-Hub/discussions) space.
- Want to file an issue or request a feature? Please go [here](https://github.com/EMOD-Hub/issues-and-discussions/issues).

## Disclaimer

The code in this repository was developed by IDM and other collaborators to support our joint research on flexible agent-based modeling.
We've made it publicly available under the MIT License to provide others with a better understanding of our research and an opportunity to build upon it for their own work. We make no representations that the code works as intended or that we will provide support, address issues that are found, or accept pull requests.
You are welcome to create your own fork and modify the code to suit your own modeling needs as permitted under the MIT License.

# Latest: Ubuntu Docker Images

Dockerfiles for building and running EMOD on Ubuntu 22.04.

## Image Overview

| File | Base OS | Purpose |
|---|---|---|
| `Dockerfile.buildenv.ubuntu` | Ubuntu 22.04 | Compile EMOD |
| `Dockerfile.runtime.ubuntu` | Ubuntu 22.04 | Run EMOD simulations |

These images are built and pushed to GHCR via the `build_docker_images.yml` pipeline as `emod-ubuntu-buildenv` and `emod-ubuntu-runtime`.

---

## `Dockerfile.buildenv.ubuntu`

Python 3.13 (via `deadsnakes` PPA), SCons, and the system packages needed to compile EMOD with GCC 11 and MPICH.

### System Packages

| Package | Purpose |
|---|---|
| `g++` | C++ compiler |
| `libc-dev` | Linux headers |
| `python3.13-dev` | Python headers |
| `libmpich-dev` | MPI runtime and headers |
| `libboost-all-dev` | Boost libraries |

---

## `Dockerfile.runtime.ubuntu`

Minimal Ubuntu 22.04 image for running EMOD simulations (without build tooling).

### System Packages

| Package | Purpose |
|---|---|
| `python3.13-dev` | Python 3.13 runtime (deadsnakes PPA) |
| `python3.13-venv` | Python 3.13 virtual environments (deadsnakes PPA) |
| `mpich` | MPI runtime |
| `libsnappy1v5` | Snappy compression runtime |
| `libboost-all-dev` | Shouldn't need this but it's providing MPI stuff |
