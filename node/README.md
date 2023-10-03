# Creating the container with the shared volume:
`docker run -it --name node -v $(pwd)/node/:/usr/src/app -p 3000:3000 node:latest bash`