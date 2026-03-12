FROM node:20-alpine As build
WORKDIR /app

COPY my-new-app/package*.json ./
COPY my-new-app .
RUN npm install

COPY . .
RUN npm run build

FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80
CMD ["nginx","-g","daemon off;"]
