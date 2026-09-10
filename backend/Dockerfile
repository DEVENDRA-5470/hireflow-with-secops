FROM node:22-alpine

# Upgrade Alpine OS packages to patch known CVEs (fixes libssl3, libcrypto3)
RUN apk update && apk upgrade --no-cache

WORKDIR /app

# Update npm CLI itself to get patched bundled dependencies (tar, pacote, brace-expansion, etc.)
RUN npm install -g npm@latest

COPY package*.json ./
RUN npm install

COPY . .

EXPOSE 3000

CMD ["npm", "start"]
