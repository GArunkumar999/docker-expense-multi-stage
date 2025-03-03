FROM node:20.18.3-alpine3.21 AS build
WORKDIR /opt/backend
COPY package.json .
COPY *.js . 
RUN npm install


FROM node:20.18.3-alpine3.21
WORKDIR /opt/backend
COPY --from=build /opt/backend /opt/backend
RUN addgroup -S expense && adduser -S expense -G expense
RUN chown -R expense:expense /opt/backend
ENV DB_HOST=mysql
EXPOSE 8080
USER expense
CMD ["node", "index.js"]




