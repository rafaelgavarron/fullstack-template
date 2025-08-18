FROM node:24-alpine3.22 AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
CMD ["npm","start"]