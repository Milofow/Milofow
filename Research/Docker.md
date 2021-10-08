## Create and deploy docker

1. create a "Dockerfile" with special commands to build your docker from your project
2. run Docker build -t username/your-project-name
3. docker tag username/your-project-name username/your-project-name
4. docker push username/your-project-name

this will create a repo on dockerhub from there you can clone it to a server. it may be required to login ```docker login``` will work if you're logged in on docker desktop






## Troubleshoot

stop Docker Desktop
stop WSL (wsl --shutdown)
unregister the docker-desktop distro (which contains binaries, but no data) with wsl --unregister docker-desktop
restart Docker Desktop
