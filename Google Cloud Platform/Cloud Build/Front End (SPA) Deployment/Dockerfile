# Use node as builder image
FROM node:14.21.0-alpine3.16 as build-stage

# Set image to be received argument when build.
# Make sure add `--build-arg` argument when building the image.
# You can edit `NAME_OF_ARGUMENT_KEY` with your own custom key name.
ARG NAME_OF_ARGUMENT_KEY
WORKDIR /app
COPY package*.json ./

# npm ci --omit=dev will installed the dependency only and ignore dev dependency.
RUN npm ci --omit=dev
COPY . .

# Set the env value from received argument when image building.
ENV CUSTOM_ENV_NAME=${NAME_OF_ARGUMENT_KEY}
RUN npm run build

# The result of the app is will be Single Page Application (SPA).
# So, we need the nginx image as web server.
FROM nginx:stable-alpine as production-stage
RUN mkdir /app

# The builder image before will generate distribution file on folder dist. Copy it to nginx, so user can access it.
COPY --from=build-stage /app/dist /app

# Add the configuration file of nginx that you've created.
COPY nginx.conf /etc/nginx/nginx.conf