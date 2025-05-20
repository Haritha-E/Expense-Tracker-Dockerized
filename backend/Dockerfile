# Stage 1: Build the backend app
FROM node:18-alpine AS build

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . ./

# Stage 2: Production image for the backend
FROM node:18-alpine

WORKDIR /app

# Install only production dependencies
COPY package*.json ./
RUN npm install --only=production

COPY --from=build /app /app

EXPOSE 5000
CMD ["node", "server.js"]
