# Dockerfile
What is a Dockerfile:

    If you want to create an image from your own code, that you can push to dockerhub, you need to create a Dockerfile for your application.
    A Dockerfile is a text document that contains all the commands a user could call on the command line to create an image.


# How to write a dockerfile

A dockerfile has 2 parts
1. Base image
2. Bunch of commands that you run on the base image (to install dependencies like Node.js)


# Let’s write our own Dockerfile
![My Screenshot](../Images/8.png)

## Common commands

WORKDIR: 
    Sets the working directory for any RUN, CMD, ENTRYPOINT, COPYinstructions that follow it.

RUN: 
    Executes any commands in a new layer on top of the current image and commits the results.

CMD: 
    Provides defaults for executing a container. There can only be one CMD instruction in a Dockerfile.

EXPOSE: 
    Informs Docker that the container listens on the specified network ports at runtime.

ENV: 
    Sets the environment variable.

COPY: 
    Allow files from the Docker host to be added to the Docker image


# Building images
Now that you have a dockerfile in your project, try building a docker image from it

    > docker build -t image_name .

Now if you try to look at your images, you should notice a new image created

    > docker images

💡 Add a .dockerignore so that node_modules don’t get copied over 

# Run images
    > docker run -p 3000:3000 image_name

# Passing in env variables

    > docker run -p 3000:3000 -e DATABASE_URL="postgres" image_name


**The -e argument let’s you send in environment variables to your node.js app**


# More commands

    > docker kill - to kill a container
    > docker exec - to exectue a command inside a container
 
Examples:
List all contents of a container folder:

    > docker exec <container_name_or_id> ls /path/to/directory

Running an Interactive Shell:

    > docker exec -it <container_name_or_id> /bin/bash


#  Pushing to dockerhub
Once you’ve created your image, you can push it to dockerhub to share it with the world.

1. Signup to dockerhub
2. Create a new repository

    ![My Screenshot](../Images/9.png)

3. Login to docker cli

    > docker login
you might have to create an access token - https://docs.docker.com/security/for-developers/access-tokens/
 

4. Push to the repository

    > docker push your_username/your_reponame:tagname
 