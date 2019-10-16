# Build phase -> build application

# >> Builder >>
FROM node:alpine as builder

WORKDIR '/app'
COPY ./package.json ./
RUN npm install 
COPY . .
RUN npm run build
# << Builder <<

#Run on server Nginx
FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
