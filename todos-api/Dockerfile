# The official Node.js 8 slim image
FROM node:8-slim

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

ENV TODO_API_PORT=8082 

EXPOSE ${TODO_API_PORT}

# Start the Node.js application
CMD ["npm", "start"]