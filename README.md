# Spring Boot containerization playground

A small, **runnable** Spring Boot REST service with Docker, Cloud Native
Buildpacks, and example deployment manifests. Cloud deployments are templates,
not validated production setups. The sample previously advertised Jib but did not
include the Jib Gradle plugin; that unsupported claim has been removed.

## Start a clean clone locally

```bash
docker compose up --build
curl -fsS http://127.0.0.1:8080/
curl -fsS http://127.0.0.1:8080/actuator/health
```

The Dockerfile compiles the application with the Gradle wrapper in a multi-stage
build; no prebuilt JAR is required. The application exposes a real HTTP endpoint
and Spring Boot Actuator health checks. Docker Compose intentionally omits
PostgreSQL because this sample application does not connect to a database.
Published ports bind to localhost.

## Other containerization methods

```bash
./gradlew bootBuildImage --imageName=spring-boot-app:buildpacks
```

## Cloud and orchestrator templates

`k8s/deployment.yaml` has resource and health probes but uses the image
placeholder `your-registry/spring-app:VERSION`; publish an image first.
OpenShift, ECS, Cloud Run, and Azure examples need registry, service accounts,
networking, and environment-specific setup before deployment. The Kubernetes
Service is ClusterIP by default. These have **not** been deployed or tested here.

GitHub Actions runs the Gradle tests and Docker build on each PR. Run the
local smoke checks above before declaring the app deployment-ready.
