### 1. Dockerfile for a node.js app
- Define base image (aka parent image)
- Define a working directory
- Copy files from local to image working directory
- Install dependencies (RUN)
- Expose Port
- Run the app (CMD)

#### RUN vs CMD
- Use RUN to execute inside image (when image creation is starting) and CMD runs in container (when container is initiated)

#### Exposing the port
- This is optional, but useful when using Docker desktop
- Docker desktop uses this for port mapping

#### dockerignore
- If you have stuff like node_modules, we dont want the copy in the Dockerfile to copy this
- So, create .dockerignore and add stuff to ignore

#### Layer caching
- So, each line in dockerfile represents a layer coz it adds sth new to the image
- For subsequent builds, layer cahing caches layers **above** the changed layer to save time/resources
- Layers below are re-run
- Therefore, it's best to have the `COPY` for source code as last layer as this is what changes most times
- (Move other layers above it... Especially `RUN npm i`. Just be sure to copy package.json before npm i)

#### Volumes
- Sync folder on host with container folder so that changes in host reflect immediately in container without having to rebuild image and stop/start container
- Map the absolute path on host to WORKDIR path on container
- (Use nodemon)
- Add another (anonymous) volume for the node_modules folder. For this, we do not specify a path on the host. This will be mapped to a folder managed by docker.

#### Docker compose
- Keeping track of multiple container configs (port mappings, volumes, container names etc...)
- So, instead of running multiple commands, we can define configs and run one command to apply them
