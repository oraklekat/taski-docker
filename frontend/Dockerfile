FROM node:18 as build

WORKDIR /app

COPY package.json package-lock.json ./
RUN npm install

COPY . .
RUN npm run build

FROM alpine:latest
RUN apk add --no-cache bash
WORKDIR /frontend_static
COPY --from=build /app/build/ .
