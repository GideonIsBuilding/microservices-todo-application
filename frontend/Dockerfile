# Node.js slim image to build app
FROM node:14 AS build

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE ${PORT:-8080}

ENV PORT=8080

CMD ["npm", "run", "dev"]