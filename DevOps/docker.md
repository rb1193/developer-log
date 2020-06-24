# Docker

To get around the issue of file permissions on Linux when using a docker volume with docker-compose, you can use a named volume rather than a local directory inside the project. Or, set the web server user's UID and GID to 1000.

To clean up old docker images that tend to hang around, you can run `docker container prune --filter=’until={timestamp}’`

When building a production image of an application that requires running an asset bundler (e.g. webpack), use multiple build stages, one for PHP (maybe with a separate composer stage) and one for Node that builds the assets.
