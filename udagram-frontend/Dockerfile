## Build
FROM node:16-alpine as build
# Create app directory
WORKDIR /usr/src/app
# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY . .
# COPY package*.json ./
RUN rm -rf package-lock.json
# RUN npm install -g yarn
RUN echo yarn --version
RUN yarn global add @ionic/cli
RUN yarn
# Bundle app source
RUN ionic build
## Run 
FROM nginx:alpine
#COPY www /usr/share/nginx/html
COPY --from=build /usr/src/app/www /usr/share/nginx/html
