FROM node:19.6-alpine
WORKDIR /usr/src/app
COPY  package*.json ./
RUN npm install
COPY . .
CMD [ "npm","run","dev"]