# Stage 1: Build with necessary tools
FROM node:18-alpine AS builder

# Install build tools ONLY in builder stage
RUN apk add --no-cache python3 make g++

WORKDIR /app
COPY package.json package-lock.json ./
RUN npm ci --production

# Stage 2: Production image
FROM node:18-alpine

WORKDIR /app
COPY --from=builder /app/node_modules ./node_modules
COPY . .

EXPOSE 8082
CMD ["node", "server.js"]