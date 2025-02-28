# Build stage
FROM node:14 as build

WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build  # Build output goes to /app/dist

CMD ["npm", "run", "dev"]