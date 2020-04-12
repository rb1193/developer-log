# Docker

To get around the issue of file permissions on Linux when using a docker volume with docker-compose, you can use a named volume rather than a local directory inside the project

To clean up old docker images that tend to hang around, you can run `docker container prune --filter=’until={timestamp}’`
