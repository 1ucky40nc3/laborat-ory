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


# Build the application using a cache mount for faster consecutive builds
RUN --mount=type=bind,source=src,target=src \
    --mount=type=bind,source=Cargo.toml,target=Cargo.toml \
    --mount=type=bind,source=Cargo.lock,target=Cargo.lock \
    set -eux; \
        cargo build --locked --release  && \
        cp "./target/release/api" /bin/server

####################################################################################
# Prod stage

FROM debian:bullseye-slim AS final

# Create a non-priviledged user to run the application
ARG UID=10001
RUN adduser \
    --disabled-password \
    --gecos "" \
    --home "/nonexistent" \
    --shell "/sbin/nologin" \
    --no-create-home \
    --uid "${UID}" \
    appuser
USER appuser

# Copy our application
COPY --from=build /bin/server /bin/

# Expose the Docker container at port 8000
EXPOSE 8000

# Run the application
CMD ["/bin/server"]

