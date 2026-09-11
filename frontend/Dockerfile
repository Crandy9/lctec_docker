FROM node:18-alpine AS build

WORKDIR /frontend

# Copy package.json and package-lock.json
COPY package*.json ./

RUN npm ci

COPY . ./

ARG ENV_FILE=.env
RUN cp $ENV_FILE .env

# places frontend/dist folder inside docker image
RUN npm run build

# Runtime stage
FROM nginx:alpine

RUN rm -rf /usr/share/nginx/html/*

COPY --from=build /frontend/dist /usr/share/nginx/html