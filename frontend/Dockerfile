# Stage 1: Build
FROM node:18-alpine AS build

WORKDIR /app

COPY package*.json ./

RUN npm ci

COPY . .

RUN npm run build

# Stage 2: Run
FROM node:18-alpine

WORKDIR /app

COPY --from=build /app/build ./build

RUN npm install -g http-server

CMD ["http-server", "-p", "8000", "/app/build"]
