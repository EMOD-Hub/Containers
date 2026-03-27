# Ubuntu Docker Images

This directory contains Dockerfiles for building and running EMOD on Ubuntu 22.04.

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
