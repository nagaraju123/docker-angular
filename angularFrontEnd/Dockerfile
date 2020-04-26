FROM node:alpine as builder

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

RUN npm run-script build
 


FROM nginx

RUN rm -rf /usr/share/nginx/html/*

COPY --from=builder /app/dist/angularFrontEnd /usr/share/nginx/html


RUN chgrp -R nginx /usr/share/nginx/html/*
RUN chmod -R g+r /usr/share/nginx/html/*

CMD ["nginx", "-g", "daemon off;"]



