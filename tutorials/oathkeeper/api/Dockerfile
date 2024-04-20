# syntax=docker/dockerfile:1

# Build a Docker Container the for the RESTful API written in Rust.
# This Dockerfile is inspired by:
#   - https://docs.docker.com/language/rust/develop/

####################################################################################
# Build stage

# Define some build args
ARG RUST_VERSION=1.77.2


FROM rust:${RUST_VERSION}-slim-bullseye AS build
WORKDIR /app

