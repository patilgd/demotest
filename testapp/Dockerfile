#build stage
FROM node:Latest as build-step
RUN mkdir -p /app
WORKDIR /app
COPY package.json /app/package.json 
RUN npm i
COPY . /app
RUN npm run build


#deploy stage

FROM nginx:alpine
COPY nginx.conf /etc/nginx/nginx.conf
COPY --from=build-step /app/dist/testapp  /usr/share/nginx/html

