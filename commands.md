#### Commands

- Build:                    docker build -t <image_name> .  
- Build with version:       docker build -t: <image_name>:<version/tag> .  
- List images:              docker images  
- Run image:                docker run <image_id/repo_name>  
- Run named container:      docker run --name <container_name> <image_id/repo_name>  
- List running containers:  docker ps  
- List all containers:      docker ps -a  
- Stop container:           docker stop <container_name/id>  
- Run named+port:           docker run --name <container_name> -p 5000:4000 -d <image_id/repo_name>  
- Run but remove after:     docker run --name <container_name> -p 5000:4000 -rm <image_id/repo_name>  
- Start stopped container:  docker start <container_name>   // no need to map port and flags again  
- Delete image:             docker image rm <image_name>       // if not in use  
- Delete image (in use):    docker image rm -f <image_name>    // even if in use  
- Delete container:         docker container rm <contaier_name>  
- Delete errthang:          docker system prune -a             // removes all images, containers, volumes  
- Attach volume:            docker run --name <container_name> -p 5000:4000 -rm -v <host_abs_path_to_folder>:<container_wkdir_path> <image_id/repo_name>  
- Attach anon. volume:      docker run --name <container_name> -p 5000:4000 -rm -v <host_abs_path_to_folder>:<container_wkdir_path> -v <container_wkdir_path/node_modules> <image_id/repo_name> // more specific for node_modules

#### Flags
- -p: PUBLISH:             for port mapping <localhost_port>:<local_port>  
- -d: DETACHED MODE:       detach the terminal from the process  
- --rm: REMOVE:            run container but remove it when stopped. Dont store it  
- -v: VOLUME:              add a volume to the container <host_abs_path>:<container_wkdir_path>