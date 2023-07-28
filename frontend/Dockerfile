FROM node:latest
WORKDIR /usr/src/app
COPY ./batchalign-web/ .
RUN yarn
RUN yarn build

EXPOSE 4173

CMD ["npx", "vite", "preview", "--host"]

