# pull official base image
FROM node:latest as build
# set working directory
WORKDIR /app
# add `/app/node_modules/.bin` to $PATH
ENV PATH /app/node_modules/.bin:$PATH
# install app dependencies
COPY package.json ./
COPY package-lock.json ./

RUN npm install --force
# add app
COPY . /app/

# Build production
RUN npm run build
RUN npm install -g serve

## Start the app on port 3006
CMD serve -s build -l 3000