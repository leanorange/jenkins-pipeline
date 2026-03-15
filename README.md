# jenkins docker agent projects

two jenkins pipeline projects demonstrating docker-as-agent configuration.

---

## project 1 — simple pipeline

a basic jenkins pipeline to verify that docker agent configuration is working.

**what it does:**
- spins up a `node:16-alpine` docker container as the build agent
- runs `node --version` inside the container to confirm it works
- tears down the container once the pipeline finishes

## project 2 — multi-stage-multi-agent pipeline

a pipeline that uses a different docker container per stage, simulating a three-tier app (frontend, backend, database).

**what it does:**
- stage 1 (backend): runs inside a `maven:3.8` container — executes `mvn --version`
- stage 2 (frontend): runs inside a `node:16-alpine` container — executes `node --version`
- stage 3 (database): runs inside a `mysql:latest` container — runs a sample sql query


## prerequisites

- ec2 instance (ubuntu)
- java / jdk installed
- jenkins installed and running on port `8080`
- docker installed on the same machine
- jenkins user added to the `docker` group
- docker pipeline plugin installed in jenkins
```
