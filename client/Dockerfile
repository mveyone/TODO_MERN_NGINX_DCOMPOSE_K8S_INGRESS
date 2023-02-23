FROM node:14-slim as builder
WORKDIR /app
COPY ./package.json ./
RUN yarn install
# RUN yarn add react-router-dom
COPY . .

EXPOSE 3000

CMD ["yarn", "start"]
RUN yarn run build

FROM nginx
EXPOSE 3000
COPY ./default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html