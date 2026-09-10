FROM node:22-alpine AS build

# Upgrade OS packages to patch known CVEs
RUN apk update && apk upgrade --no-cache

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .


# ---- Final runtime stage: no npm CLI, no build tools ----
FROM node:22-alpine

RUN apk update && apk upgrade --no-cache

WORKDIR /app

# Copy only what's needed to run the app — node_modules and source code
COPY --from=build /app ./

EXPOSE 3000

CMD ["node", "src/index.js"]
