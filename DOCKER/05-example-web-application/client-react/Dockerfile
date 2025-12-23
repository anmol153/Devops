FROM node:19.4-bullseye as build

WORKDIR /src/app

COPY ./package*.json .

RUN --mount=type=cache,target=/usr/src/app/.npm \
    npm set cache /usr/app/.npm && \
    npm ci

COPY . .

RUN npm run build 
FROM nginx:1.22-alpine
WORKDIR /src/app
COPY nginx.conf /etc/nginx/conf.d/default.conf

COPY --from=build usr/app /usr/share/nginx/html

EXPOSE 80


