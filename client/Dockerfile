FROM node:alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
RUN rm -rf /usr/share/nginx/html/*
COPY ./nginx/nginx-default-prod.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
EXPOSE 3000
#CMD [ "nginx", "-g", "deamon=off;" ]
