# 🐳 Dockerfile Cheatsheet

---

## FROM

- Sets base image for build.
- Usage:
  ```dockerfile
  FROM ubuntu
  FROM node:18
  FROM alpine@sha256:...
  ```
- Must be first non-comment instruction. Can appear multiple times for multi-stage builds.

---

## MAINTAINER

- Sets image author (deprecated, use LABEL).
  ```dockerfile
  MAINTAINER "Your Name"
  ```

---

## RUN

- Executes commands in build.
  ```dockerfile
  RUN apt-get update
  RUN ["executable", "param1"]
  ```
- Shell form uses `/bin/sh -c` by default. Exec form avoids shell parsing.

---

## CMD

- Default command for container.
  ```dockerfile
  CMD ["executable", "param1"]
  CMD ["param1"]         # As default args to ENTRYPOINT
  CMD command param1     # Shell form
  ```
- Only last CMD takes effect.

---

## LABEL

- Adds metadata to image.
  ```dockerfile
  LABEL version="1.0" description="My image"
  ```

---

## EXPOSE

- Documents ports container listens on.
  ```dockerfile
  EXPOSE 80 443
  ```
- Does not publish ports to host.

---

## ENV

- Sets environment variables.
  ```dockerfile
  ENV NODE_ENV production
  ENV PATH="/usr/local/bin:$PATH"
  ```

---

## ADD

- Copies files, directories, URLs into image.
  ```dockerfile
  ADD src/ /app/
  ADD https://example.com/file.txt /file.txt
  ```

---

## COPY

- Copies files/directories from build context.
  ```dockerfile
  COPY . /app/
  COPY ["src", "dest"]
  ```

---

## ENTRYPOINT

- Configures container as executable.
  ```dockerfile
  ENTRYPOINT ["executable", "param1"]
  ENTRYPOINT command param1
  ```
- Arguments to `docker run` override CMD defaults.

---

## VOLUME

- Defines mount points for external volumes.
  ```dockerfile
  VOLUME ["/data"]
  ```

---

## USER

- Sets user/UID for following instructions.
  ```dockerfile
  USER appuser
  ```

---

## WORKDIR

- Sets working directory for following instructions.
  ```dockerfile
  WORKDIR /app
  ```

---

## ARG

- Defines build-time variables.
  ```dockerfile
  ARG VERSION=1.0
  ```
- Passed with `docker build --build-arg`.

---

## ONBUILD

- Adds trigger for child builds.
  ```dockerfile
  ONBUILD COPY . /src
  ```

---

## STOPSIGNAL

- Sets signal for container shutdown.
  ```dockerfile
  STOPSIGNAL SIGKILL
  ```

---

## HEALTHCHECK

- Defines container health check.
  ```dockerfile
  HEALTHCHECK --interval=30s CMD curl -f http://localhost/ || exit 1
  HEALTHCHECK NONE
  ```

---

## SHELL

- Overrides default shell for shell-form commands.
  ```dockerfile
  SHELL ["bash", "-c"]
  ```

---
