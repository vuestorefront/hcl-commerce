FROM node:14 AS build

WORKDIR /var/www

COPY . .

RUN cd docs \
  && npm install \
  && sed -i "s/base: '\/',/base: '\/hcl-commerce\/',/g" ./.vuepress/config.js \
  && cat ./.vuepress/config.js \
  && npm run build

FROM nginx

COPY --from=build /var/www/docs/.vuepress/dist /usr/share/nginx/html/hcl-commerce
