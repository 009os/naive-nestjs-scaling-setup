# app/Dockerfile
FROM node:18

WORKDIR /usr/src/app

COPY . .

RUN npm install

RUN npm run build

CMD ["npm", "run", "start:prod"] 