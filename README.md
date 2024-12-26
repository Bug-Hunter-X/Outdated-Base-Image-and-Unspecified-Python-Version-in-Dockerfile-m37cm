# Dockerfile Bug: Outdated Base Image and Unspecified Python Version

This repository demonstrates a common bug in Dockerfiles: using an outdated base image and failing to specify a Python version. This can lead to security vulnerabilities, inconsistencies across environments, and build failures.

## Bug Description
The original `Dockerfile` uses `ubuntu:latest`, which is a very generic and potentially outdated base image. It also doesn't explicitly define the Python version, which can cause unexpected behavior if different Python versions are available on different systems.

## Bug Solution
The `Dockerfile_fixed` provides a solution by:

1.  Using a more specific and updated base image (`ubuntu:22.04`).
2.  Creating a virtual environment for better dependency management and consistency.
3.  Explicitly installing a specific Python version.
4.  Copying the project requirements after creating the virtual environment to ensure they are installed within this environment.

## How to reproduce
1.  Clone the repo
2.  Build the original `Dockerfile` using `docker build -t outdated-image -f Dockerfile .`
3.  Build the fixed `Dockerfile` using `docker build -t updated-image -f Dockerfile_fixed .`
4.  Inspect the differences in both builds, noting the package versions and image sizes.