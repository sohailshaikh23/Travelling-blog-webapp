################################### Stage 1: Build stage named as frontend-builder #######################
# Using node:21 as base image for the build stage
FROM node:21 AS frontend-builder

# information about maintainer
LABEL maintainer="sohailshaikh125@gmail.com"

# creating current working directory 
WORKDIR /app

# Copy the application code into the /app directory
COPY . .

# install the require dependencies   
RUN npm install


######################################### Stage 2 : Final stage ######################################
#Using node:21-slim as base image for the final stage to make the image a light weight image
FROM node:21-slim

# creating current working directory as /app
WORKDIR /app

# copy only the require files from the frontend-builder stage to the Current stage
COPY --from=frontend-builder /app .

#Copy the environment varaible file 
COPY .env.sample .env.local

# Exposing the port 5173 for the application
EXPOSE 5173

# Provide the default command to run the application
CMD ["npm","run","dev","--","--host"]
