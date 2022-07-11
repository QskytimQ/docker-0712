FROM localhost:32443/dockerhub/library/node:12-stretch AS builder
COPY app /home/node/app
WORKDIR /home/node/app
RUN ls && \
    npm install && \
    npm run build

FROM localhost:32443/dockerhub/library/nginx:1.19
COPY --from=builder /home/node/app/dist/ /usr/share/nginx/html/
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
