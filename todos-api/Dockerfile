FROM node:18-alpine
WORKDIR /app

# Copy package.json first to leverage Docker caching
COPY package.json package-lock.json ./
RUN npm install

# Copy the rest of the application files
COPY . .

EXPOSE 8082
CMD ["node", "server.js"]