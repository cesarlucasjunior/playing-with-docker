FROM node:latest

WORKDIR /usr/src/app
COPY . .
RUN npm install express --save
EXPOSE 3000
CMD [ "node", "index.js"]