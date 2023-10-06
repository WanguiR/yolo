## Choice of the base image on which to build each container.
Built three containers:
 1. yolo-frontend-1  built from image yolo-frontend-app:v1.0.1
 2. yolo-backend-1  built from image yolo-backend-app:v1.0.1
 3. yolo-mongo-1    built from image mongo:6.0
 I chose my images based on size so as to run and build scaled containers that do not take much of space 
 I also pulled mongo version 6 image from dockerhub instead of just using latest tag
 I then pushed the two yolo images to dockerhub on different repositories namely #yolo-backend and #yolo-frontend 

## Dockerfile directives used in the creation and running of each container.
Image for the application is `FROM node:14-Alpine`
set the working directory using `WORKDIR`
`COPY` command to copy files like package.json and application code
Run the folllowing command to install the dependencies 
 `npm install`
Run the folllowing to start the app
 `npm start`

## Docker-compose Networking (Application port allocation and a bridge network implementation) where necessary.
Created a network named `my network` with the driver `bridge`
Allocated different ports to the images that built the containers,Initially I had allocated port 8080 but noticed it was in use by another service so I switched that
Ports allocated for 
1. yolo-frontend-1 container - 8888:80
2. yolo-backend-1 container - 3001:3000

## Git workflow used to achieve the task.
I forked the repo 
Cloned the repository on my local machine using `git clone` command and then initiated git `git init `
Opened the repo on VS code using `code .` command
Wrote the dockercompose.yml and dockerfiles for both backend and client modules
Used `git add .` to stage changes and new files added to the project eg. .dockerignore .env explanation.md
Used `git commit -m "*message*"` to commit any new changes made and for specific files I added `./directory or filename` 
Used `git push` to push changes made locally to my github repository

## Successful running of the applications and if not, debugging measures applied.


## Good practices such as Docker image tag naming standards for ease of identification of images and containers. 
Tagged my images by adding versions
The below images were the fist version which were too large.
`yolo-frontend-app       v1.0.0  ` 
`yolo-backend-app        v1.0.0  ` 
`node:14`
The below images are the second version tag after I added a .dockerignore file to ignore unnecessary files during building and reduce size. Also used a lighter Node image here to reduce footprint
`wanguir/yolo-frontend   v1.0.1 `
`wanguir/yolo-backend    v1.0.1 `
`node:14-Alpine`

## There is a screenshot of your deployed image on DockerHub, clearly showing the version of the image
https://drive.google.com/drive/folders/17nRIVWWGw5oCr2LJ129uvF2bUen0vIbq?usp=sharing 