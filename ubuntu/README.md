# Ubuntu Docker Images

This directory contains Dockerfiles for building and running EMOD on Ubuntu 26.04.

## Image Overview

| File | Base OS | Purpose |
|---|---|---|
| `Dockerfile.buildenv.ubuntu` | Ubuntu 26.04 | Compile EMOD |
| `Dockerfile.runtime.ubuntu` | Ubuntu 26.04 | Run EMOD simulations |

These images are built and pushed to GHCR via the `build_docker_images.yml` pipeline as `emod-ubuntu-buildenv` and `emod-ubuntu-runtime`.

---

## `Dockerfile.buildenv.ubuntu`

Python 3.14, SCons, and the system packages needed to compile EMOD with GCC 15 and MPICH.

### System Packages

| Package | Purpose |
|---|---|
| `g++` | C++ compiler |
| `libc-dev` | Linux headers |
| `python3-dev` | Python headers |
| `libmpich-dev` | MPI runtime and headers |
| `libboost-dev` | Boost headers |

---

## `Dockerfile.runtime.ubuntu`

Minimal Ubuntu 26.04 image for running EMOD simulations (without build tooling).

### System Packages

| Package | Purpose |
|---|---|
| `mpich` | MPI runtime |
| `libsnappy1v5` | Snappy compression runtime |
