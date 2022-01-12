FROM node:16-alpine as builder

WORKDIR '/app'
COPY ./package.json ./

RUN npm install

COPY . .

RUN npm run build

############################## the second from statment finishes the forst stage
#/app/build <-- all the important stuff

FROM nginx
#expose is a way to communicate 
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
## copy from another phase, which folder, to where
COPY --from=builder /app/build usr/share/nginx/html
