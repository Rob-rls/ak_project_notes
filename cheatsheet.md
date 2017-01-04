## Docker
- Set up daemon (required for each terminal pane)
  - `docker-machine start default`
  - `docker-machine env`
  - `eval $(docker-machine env default)`
- build an image `docker build -t <name> <tag>` eg docker build -t Rob-rls/webapp .
- remove an image `docker rmi -f <image name>`
- run an interactive session `docker exec -i -t <uuid> cmd ...`
- Dockerfile commands
  - `FROM` base image to copy
  - `ADD <src> <dest>` adds files from src to the dest on the image
  - `EXPOSE` port to use on image
  - `CMD` default command to run if no command given when starting an image.

## Docker Compose
- Start containters (requires a docke-compose.yml)
  - `docker-compose up -d` (-d to run in background)
- Execute a script on a runing container
  - `docker-compse exec <appname> <path/to/script/on/container.sh>`

## CI
- Start Vagrant
  - `vagrant up default`
- Set target for fly
  - `fly -t lite login -c http://192.168.100.4:8080`
- Set pipeline `fly -t lite set-pipeline -p hello-world -c hello.yml`
#### Example using the PCS project to test locally
- Set target
  - `fly -t pcs login --concourse-url https://ci.armakuni.co.uk/ -n pcs`
- Sync with remote
  - `fly -t pcs sync`
- get save remote pipeline locally
  - `fly -t pcs get-pipeline -p pcs-pipeline > pipeline.yml`
- Execute task to check if local changes pass (Must use a local yml file for the task)
  - `fly -t pcs execute -c task.yml -i pcs-applicant-app=.`
- Set the remote pipeline using a config and loads variables from a file
  - `fly -t pcs set-pipeline -p pcs-pipeline -c ./cci/pcs.yml -l ./private/cci_private_vars.yml`




## Cloud Foundry
- see apps
  - `cf apps`
- deploy app `cf push` - must be in the project directory
- view logs `cf logs <app name> --recent`
- environment variables
  - `cf set-env <app name> <var name> <var value>`
  - `cf env <app name>` to view the env variables
- restart the app `cf restart <app name>`
- Services
  - see services on marketplace `cf marketplace`
  - create a service instance `cf create-service`
  - bind the service `cf bind-service`
  - restage the app `cf restage`
- Scaling
  - `cf scale`
  - -i instances
  - -m memory limit
  - -k disk space limit
- domains and routes
  - create a domain for an org `cf create-domain`
  - create a route `cf create-route`
  - map the route to the app `cf map-route`
- Deploying non-web components (workers, etc..)
  - `cf push <app name> --no-route -u none -f <path to manifest>`
