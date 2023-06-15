# [Choice] Debian OS version (use bullseye on local arm64/Apple Silicon): buster, bullseye
ARG VARIANT="bullseye"
FROM rust:1-${VARIANT}

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get upgrade -y \
    # Remove imagemagick due to https://security-tracker.debian.org/tracker/CVE-2019-10131
    && apt-get purge -y imagemagick imagemagick-6-common \
    && curl -fsSL https://deb.nodesource.com/setup_16.x | bash - \
    && apt-get install nodejs \
    && apt-get -y install build-essential clang 

# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
   # && apt-get -y install g++-mingw-w64-x86-64 

RUN rustup target add aarch64-unknown-linux-gnu